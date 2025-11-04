---
title: wireless
---

{{< badge metrics >}}

{{< callout type="info" >}}
Linux only
{{< /callout >}}

Collecting metrics about wireless, e.g. the current status of the device, the quality of reception, the number of
packets...

## Example
```yaml
# Duration between each collecting.
#
# Optional
interval: 15s
```

## Output 
```text
# HELP wifi_interface_frequency_hertz The current frequency a WiFi interface is operating at, in hertz
# TYPE wifi_interface_frequency_hertz gauge
wifi_interface_frequency_hertz{device="xxxxxx"} 5745000000
# HELP wifi_station_beacon_loss_total The total number of times a station has detected a beacon loss
# TYPE wifi_station_beacon_loss_total counter
wifi_station_beacon_loss_total{device="xxxxxx",mac="11:22:33:44:55:66"} 0
# HELP wifi_station_connected_seconds_total The total number of seconds a station has been connected to an access point
# TYPE wifi_station_connected_seconds_total counter
wifi_station_connected_seconds_total{device="xxxxxx",mac="11:22:33:44:55:66"} 11152
# HELP wifi_station_inactive_seconds The number of seconds since any wireless activity has occurred on a station
# TYPE wifi_station_inactive_seconds gauge
wifi_station_inactive_seconds{device="xxxxxx",mac="11:22:33:44:55:66"} 11.093
# HELP wifi_station_info Labeled WiFi interface station information as provided by the operating system
# TYPE wifi_station_info gauge
wifi_station_info{bssid="11:22:33:44:55:66",device="xxxxxx",mode="client",ssid="hlywtt"} 1
# HELP wifi_station_receive_bits_per_second The current WiFi receive bitrate of a station, in bits per second
# TYPE wifi_station_receive_bits_per_second gauge
wifi_station_receive_bits_per_second{device="xxxxxx",mac="11:22:33:44:55:66"} 14400000
# HELP wifi_station_receive_bytes_total The total number of bytes received by a WiFi station
# TYPE wifi_station_receive_bytes_total counter
wifi_station_receive_bytes_total{device="xxxxxx",mac="11:22:33:44:55:66"} 2518683
# HELP wifi_station_received_packets_total The total number of packets received by a station
# TYPE wifi_station_received_packets_total counter
wifi_station_received_packets_total{device="xxxxxx",mac="11:22:33:44:55:66"} 15695
# HELP wifi_station_signal_dbm The current WiFi signal strength, in decibel-milliwatts (dBm)
# TYPE wifi_station_signal_dbm gauge
wifi_station_signal_dbm{device="xxxxxx",mac="11:22:33:44:55:66"} -76
# HELP wifi_station_transmit_bits_per_second The current WiFi transmit bitrate of a station, in bits per second
# TYPE wifi_station_transmit_bits_per_second gauge
wifi_station_transmit_bits_per_second{device="xxxxxx",mac="11:22:33:44:55:66"} 58500000
# HELP wifi_station_transmit_bytes_total The total number of bytes transmitted by a WiFi station
# TYPE wifi_station_transmit_bytes_total counter
wifi_station_transmit_bytes_total{device="xxxxxx",mac="11:22:33:44:55:66"} 1105867
# HELP wifi_station_transmit_failed_total The total number of times a station has failed to send a packet
# TYPE wifi_station_transmit_failed_total counter
wifi_station_transmit_failed_total{device="xxxxxx",mac="11:22:33:44:55:66"} 1
# HELP wifi_station_transmit_retries_total The total number of times a station has had to retry while sending a packet
# TYPE wifi_station_transmit_retries_total counter
wifi_station_transmit_retries_total{device="xxxxxx",mac="11:22:33:44:55:66"} 1486
# HELP wifi_station_transmitted_packets_total The total number of packets transmitted by a station
# TYPE wifi_station_transmitted_packets_total counter
wifi_station_transmitted_packets_total{device="xxxxxx",mac="11:22:33:44:55:66"} 3797
```
