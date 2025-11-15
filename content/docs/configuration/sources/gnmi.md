---
title: gnmi
---

{{< badge "metrics" >}}&nbsp;

{{< callout type="info" >}}
Only support `proto` encoding, you can check this by the capabilities response
```console
gnmic -a <mgmt-address> \
  --skip-verify \
  -u <username> \
  -p <password> \
  -e proto \
  cap
```
{{< /callout >}}

To config gnmi source, you'd better install [gnmic](https://gnmic.openconfig.net/install/) to get the correct path to subscribe

```console
gnmic -a <mgmt-address> \
  --skip-verify \
  -u <username> \
  -p <password> \
  -e proto \
  get \
  --path /openconfig/interfaces/interface/subinterfaces/subinterface/state/counters
```

you'll got something like this
```json
[
  {
    "source": "172.20.20.2:57400",
    "timestamp": 1763226695134961250,
    "time": "2025-11-16T01:11:35.13496125+08:00",
    "updates": [
      {
        "Path": "interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/in-octets",
        "values": {
          "interfaces/interface/subinterfaces/subinterface/state/counters/in-octets": 104425
        }
      },
      {
        "Path": "interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/in-pkts",
        "values": {
          "interfaces/interface/subinterfaces/subinterface/state/counters/in-pkts": 1040
        }
      },
      {
        "Path": "interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/in-discards",
        "values": {
          "interfaces/interface/subinterfaces/subinterface/state/counters/in-discards": 1040
        }
      },
      {
        "Path": "interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/out-octets",
        "values": {
          "interfaces/interface/subinterfaces/subinterface/state/counters/out-octets": 686905
        }
      },
      {
        "Path": "interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/out-pkts",
        "values": {
          "interfaces/interface/subinterfaces/subinterface/state/counters/out-pkts": 943
        }
      },
      {
        "Path": "interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/out-discards",
        "values": {
          "interfaces/interface/subinterfaces/subinterface/state/counters/out-discards": 0
        }
      }
    ]
  }
]
```

The metric name is generated from path, simply replace `/` and `-` with `_`, and add proper tags.
e.g.
```text
interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/out-octets
```
to 
```text
interfaces_interface_state_counters_out_octets{name="mgmt0"} 4355
```

## Example
```yaml
# Address and port of the gNMI GRPC server
#
# Required
endpoints:
  - http://172.20.20.2:57400

# Configures the TLS options for incoming/outgoing connections.
#
# Optional
tls:
  # Absolute path to an additional CA certificate file, in DER or PEM
  # format(X.509), or an inline CA certificate in PEM format.
  #
  # Optional
  ca: null

  # Absolute path to a certificate file used to identify this connection,
  # in DER or PEM format (X.509) or PKCS#12, or an inline certificate in
  # PEM format. If this is set and is not a PKCS#12 archive, "key_file"
  # must also be set.
  #
  # Optional
  cert: null

  # Absolute path to a private key file used to identify this connection,
  # in DER or PEM format (PKCS#8), or an inline private key in PEM format.
  # If this is set, "crt_file" must also be set.
  #
  # Optional
  key: null

  # Pass phrase used to unlock the encrypted key file. This has no effect
  # unless "key" is set.
  #
  # Optional
  key_pass: null

  # Enables certificate verification.
  # If enabled, certificates must not be expired and must be issued by a trusted issuer.
  # This verification operates in a hierarchical manner, checking that the leaf certificate
  # (the certificate presented by the client/server) is not only valid, but that the issuer
  # of that certificate is also valid, and so on until the verification process reaches a
  # root certificate.
  # 
  # Relevant for both incoming and outgoing connections.
  # 
  # Do NOT set this to false unless you understand the risks of not verifying the
  # validity of certificates.
  #
  # Optional
  verify_certificate: true

  # Enables hostname verification. If enabled, the hostname used to connect to the remote
  # host must be present in the TLS certificate presented by the remote host, either as the
  # Common Name or as an entry in the Subject Alternative Name extension.
  # 
  # Only relevant for outgoing connections.
  # 
  # Do NOT set this to false unless you understand the risks of not verifying the remote hostname.
  #
  # Optional
  verify_hostname: true

# Auth credentials
#
# Optional
auth:
  # The authentication username.
  #
  # Required
  username: ""

  # The authentication password.
  #
  # Required
  password: ""

interval: 15s

subscriptions:
  # openconfig-interfaces
  - path: /openconfig/interfaces/interface/state/counters
  - path: /openconfig/interfaces/interface/subinterfaces/subinterface/state/counters
  # openconfig-lldp
  - path: /openconfig/lldp/state/counters
```

## Output
```text
# HELP interfaces_interface_state_counters_carrier_transitions /interfaces/interface[name=ethernet-1/1]/state/counters/carrier-transitions
# TYPE interfaces_interface_state_counters_carrier_transitions gauge
interfaces_interface_state_counters_carrier_transitions{name="ethernet-1/1"} 1
interfaces_interface_state_counters_carrier_transitions{name="mgmt0"} 1
# HELP interfaces_interface_state_counters_in_broadcast_pkts /interfaces/interface[name=ethernet-1/1]/state/counters/in-broadcast-pkts
# TYPE interfaces_interface_state_counters_in_broadcast_pkts gauge
interfaces_interface_state_counters_in_broadcast_pkts{name="ethernet-1/1"} 0
interfaces_interface_state_counters_in_broadcast_pkts{name="mgmt0"} 0
# HELP interfaces_interface_state_counters_in_discards /interfaces/interface[name=ethernet-1/1]/state/counters/in-discards
# TYPE interfaces_interface_state_counters_in_discards gauge
interfaces_interface_state_counters_in_discards{name="ethernet-1/1"} 5
interfaces_interface_state_counters_in_discards{name="mgmt0"} 20
# HELP interfaces_interface_state_counters_in_errors /interfaces/interface[name=ethernet-1/1]/state/counters/in-errors
# TYPE interfaces_interface_state_counters_in_errors gauge
interfaces_interface_state_counters_in_errors{name="ethernet-1/1"} 0
interfaces_interface_state_counters_in_errors{name="mgmt0"} 0
# HELP interfaces_interface_state_counters_in_fcs_errors /interfaces/interface[name=ethernet-1/1]/state/counters/in-fcs-errors
# TYPE interfaces_interface_state_counters_in_fcs_errors gauge
interfaces_interface_state_counters_in_fcs_errors{name="ethernet-1/1"} 0
interfaces_interface_state_counters_in_fcs_errors{name="mgmt0"} 0
# HELP interfaces_interface_state_counters_in_multicast_pkts /interfaces/interface[name=ethernet-1/1]/state/counters/in-multicast-pkts
# TYPE interfaces_interface_state_counters_in_multicast_pkts gauge
interfaces_interface_state_counters_in_multicast_pkts{name="ethernet-1/1"} 5
interfaces_interface_state_counters_in_multicast_pkts{name="mgmt0"} 0
# HELP interfaces_interface_state_counters_in_octets /interfaces/interface[name=ethernet-1/1]/state/counters/in-octets
# TYPE interfaces_interface_state_counters_in_octets gauge
interfaces_interface_state_counters_in_octets{name="ethernet-1/1"} 350
interfaces_interface_state_counters_in_octets{name="mgmt0"} 2237
# HELP interfaces_interface_state_counters_in_pkts /interfaces/interface[name=ethernet-1/1]/state/counters/in-pkts
# TYPE interfaces_interface_state_counters_in_pkts gauge
interfaces_interface_state_counters_in_pkts{name="ethernet-1/1"} 5
interfaces_interface_state_counters_in_pkts{name="mgmt0"} 24
# HELP interfaces_interface_state_counters_in_unicast_pkts /interfaces/interface[name=ethernet-1/1]/state/counters/in-unicast-pkts
# TYPE interfaces_interface_state_counters_in_unicast_pkts gauge
interfaces_interface_state_counters_in_unicast_pkts{name="ethernet-1/1"} 0
interfaces_interface_state_counters_in_unicast_pkts{name="mgmt0"} 4
# HELP interfaces_interface_state_counters_out_broadcast_pkts /interfaces/interface[name=ethernet-1/1]/state/counters/out-broadcast-pkts
# TYPE interfaces_interface_state_counters_out_broadcast_pkts gauge
interfaces_interface_state_counters_out_broadcast_pkts{name="ethernet-1/1"} 0
interfaces_interface_state_counters_out_broadcast_pkts{name="mgmt0"} 6
# HELP interfaces_interface_state_counters_out_discards /interfaces/interface[name=ethernet-1/1]/state/counters/out-discards
# TYPE interfaces_interface_state_counters_out_discards gauge
interfaces_interface_state_counters_out_discards{name="ethernet-1/1"} 0
interfaces_interface_state_counters_out_discards{name="mgmt0"} 0
# HELP interfaces_interface_state_counters_out_errors /interfaces/interface[name=ethernet-1/1]/state/counters/out-errors
# TYPE interfaces_interface_state_counters_out_errors gauge
interfaces_interface_state_counters_out_errors{name="ethernet-1/1"} 0
interfaces_interface_state_counters_out_errors{name="mgmt0"} 0
# HELP interfaces_interface_state_counters_out_multicast_pkts /interfaces/interface[name=ethernet-1/1]/state/counters/out-multicast-pkts
# TYPE interfaces_interface_state_counters_out_multicast_pkts gauge
interfaces_interface_state_counters_out_multicast_pkts{name="ethernet-1/1"} 13
interfaces_interface_state_counters_out_multicast_pkts{name="mgmt0"} 32
# HELP interfaces_interface_state_counters_out_octets /interfaces/interface[name=ethernet-1/1]/state/counters/out-octets
# TYPE interfaces_interface_state_counters_out_octets gauge
interfaces_interface_state_counters_out_octets{name="ethernet-1/1"} 2236
interfaces_interface_state_counters_out_octets{name="mgmt0"} 4355
# HELP interfaces_interface_state_counters_out_pkts /interfaces/interface[name=ethernet-1/1]/state/counters/out-pkts
# TYPE interfaces_interface_state_counters_out_pkts gauge
interfaces_interface_state_counters_out_pkts{name="ethernet-1/1"} 13
interfaces_interface_state_counters_out_pkts{name="mgmt0"} 40
# HELP interfaces_interface_state_counters_out_unicast_pkts /interfaces/interface[name=ethernet-1/1]/state/counters/out-unicast-pkts
# TYPE interfaces_interface_state_counters_out_unicast_pkts gauge
interfaces_interface_state_counters_out_unicast_pkts{name="ethernet-1/1"} 0
interfaces_interface_state_counters_out_unicast_pkts{name="mgmt0"} 2
# HELP interfaces_interface_subinterfaces_subinterface_state_counters_in_discards /interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/in-discards
# TYPE interfaces_interface_subinterfaces_subinterface_state_counters_in_discards gauge
interfaces_interface_subinterfaces_subinterface_state_counters_in_discards{index="0",name="mgmt0"} 23
# HELP interfaces_interface_subinterfaces_subinterface_state_counters_in_octets /interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/in-octets
# TYPE interfaces_interface_subinterfaces_subinterface_state_counters_in_octets gauge
interfaces_interface_subinterfaces_subinterface_state_counters_in_octets{index="0",name="mgmt0"} 2195
# HELP interfaces_interface_subinterfaces_subinterface_state_counters_in_pkts /interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/in-pkts
# TYPE interfaces_interface_subinterfaces_subinterface_state_counters_in_pkts gauge
interfaces_interface_subinterfaces_subinterface_state_counters_in_pkts{index="0",name="mgmt0"} 23
# HELP interfaces_interface_subinterfaces_subinterface_state_counters_out_discards /interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/out-discards
# TYPE interfaces_interface_subinterfaces_subinterface_state_counters_out_discards gauge
interfaces_interface_subinterfaces_subinterface_state_counters_out_discards{index="0",name="mgmt0"} 0
# HELP interfaces_interface_subinterfaces_subinterface_state_counters_out_octets /interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/out-octets
# TYPE interfaces_interface_subinterfaces_subinterface_state_counters_out_octets gauge
interfaces_interface_subinterfaces_subinterface_state_counters_out_octets{index="0",name="mgmt0"} 1742
# HELP interfaces_interface_subinterfaces_subinterface_state_counters_out_pkts /interfaces/interface[name=mgmt0]/subinterfaces/subinterface[index=0]/state/counters/out-pkts
# TYPE interfaces_interface_subinterfaces_subinterface_state_counters_out_pkts gauge
interfaces_interface_subinterfaces_subinterface_state_counters_out_pkts{index="0",name="mgmt0"} 21
# HELP lldp_state_counters_entries_aged_out /lldp/state/counters/entries-aged-out
# TYPE lldp_state_counters_entries_aged_out gauge
lldp_state_counters_entries_aged_out 0
# HELP lldp_state_counters_frame_discard /lldp/state/counters/frame-discard
# TYPE lldp_state_counters_frame_discard gauge
lldp_state_counters_frame_discard 0
# HELP lldp_state_counters_frame_error_in /lldp/state/counters/frame-error-in
# TYPE lldp_state_counters_frame_error_in gauge
lldp_state_counters_frame_error_in 0
# HELP lldp_state_counters_frame_in /lldp/state/counters/frame-in
# TYPE lldp_state_counters_frame_in gauge
lldp_state_counters_frame_in 0
# HELP lldp_state_counters_frame_out /lldp/state/counters/frame-out
# TYPE lldp_state_counters_frame_out gauge
lldp_state_counters_frame_out 26
# HELP lldp_state_counters_tlv_accepted /lldp/state/counters/tlv-accepted
# TYPE lldp_state_counters_tlv_accepted gauge
lldp_state_counters_tlv_accepted 0
# HELP lldp_state_counters_tlv_discard /lldp/state/counters/tlv-discard
# TYPE lldp_state_counters_tlv_discard gauge
lldp_state_counters_tlv_discard 0
# HELP lldp_state_counters_tlv_unknown /lldp/state/counters/tlv-unknown
# TYPE lldp_state_counters_tlv_unknown gauge
lldp_state_counters_tlv_unknown 0
```