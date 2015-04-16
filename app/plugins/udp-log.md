---
title: Plugins - UDP Log
show_faq: true
id: page-plugin
header_title: UDP Log
header_icon: /assets/images/icons/plugins/udp-log.png
header_caption: logging
breadcrumbs:
  Plugins: /plugins
  UDP Log: /plugins/udp-log/
---

---

#### Log request and response data to an UDP server

---

## Installation

<!---
Make sure every Kong server in your cluster has the required dependency by executing:

```bash
$ kong install udplog
```
-->

Add the plugin to the list of available plugins on every Kong server in your cluster by editing the [kong.yml](/docs/{{site.data.kong_latest}}/getting-started/configuration) configuration file

```yaml
plugins_available:
  - udplog
```

Every node in the Kong cluster should have the same `plugins_available` property value.

## Configuration

Configuring the plugin is straightforward, you can add it on top of an [API](/docs/{{site.data.kong_latest}}/api/#api-object) (or [Consumer](/docs/{{site.data.kong_latest}}/api/#consumer-object)) by executing the following request on your Kong server:

```bash
curl -d "name=udplog&api_id=API_ID&value.host=127.0.0.1&value.port=9999&value.timeout=1000" http://kong:8001/plugins_configurations/
```

| parameter       | description                                                                                 |
| --------------- |-------------------------------------------------------------------------------------------- |
| name            | The name of the plugin to use, in this case: `udplog`                                       |
| api_id          | The API ID that this plugin configuration will target                                       |
| *consumer_id*   | Optionally the CONSUMER ID that this plugin configuration will target                       |
| `value.host`    | The IP address or host name to send data to                                                 |
| `value.port`    | The port to send data to on the final server                                                |
| `value.timeout` | Default `10000`. An optional timeout in milliseconds when sending data to the final server  |