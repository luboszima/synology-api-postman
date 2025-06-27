# synology-api-postman
Postman collection for Synology API

## Import Collection

Here is documentation https://learning.postman.com/docs/getting-started/importing-and-exporting/importing-data/

## Initial Setup

When you import the collection, you will need to set up the collection variables.
![initial setup](/imgs/postman_collection_init_steps.png)


## Current APIs in collection

### SYNO.Docker.Log

This API provides access to the event logs of Container Manager. For example if you start, stop, build or clean your project these event will be visible in this API.

#### list

Get the list of event logs.

- Request method: POST
- Request Body x-www-form-urlencoded:

```json 
{
  "api": "SYNO.Docker.Log",
  "method": "list",
  "version": "1",
  "action": "\"load\"",
  "offset": "0",
  "limit": "1000",
  "sort_by": "\"time\"",
  "sort_dir": "\"DESC\"",
  "loglevel": "\"\"",
  "filter_content": "\"\"",
  "datefrom": "0",
  "dateto": "0"
}
```

#### clear

Clear the event logs.

- Request method: POST
- Request Body x-www-form-urlencoded:

```json 
{
  "api": "SYNO.Docker.Log",
  "method": "clear",
  "version": "1"
}
```

#### export

Export the event logs in HTML or CSV format.

- Request method: GET
- Request Body query parameters:

```json 
{
  "api": "SYNO.Docker.Log",
  "method": "export",
  "version": "1",
  "format": "\"html\"",
  "loglevel": "\"\"",
  "filter_content": "\"\"",
  "datefrom": "0",
  "dateto": "0",
  "SynoToken": "{{SYNO_TOKEN}}"
}
```

### SYNO.Docker.Network

This API provides access to the network management of Container Manager. You can create, delete, and manage networks for your containers.

#### list

List of networks.

- Request method: POST
- Request Body query parameters:

```json 
{
  "api": "SYNO.Docker.Network",
  "method": "list",
  "version": "1"
}
```

#### create

Create a new network.

- Request method: POST
- Request Body query parameters:

```json 
{
  "api": "SYNO.Docker.Network",
  "method": "create",
  "version": "1",
  "name": "\"test2\"",
  "subnet": "\"10.0.0.5/16\"",
  "iprange": "\"10.0.0.5/16\"",
  "gateway": "\"10.0.0.1\"",
  "disable_masquerade": "false",
  "enable_ipv6": "false",
  "ipv6_subnet": "\"2001:db8:abcd:0012::/64\"",
  "ipv6_iprange": "\"2001:db8:abcd:12::1/64\"",
  "ipv6_gateway": "\"2001:db8:abcd:12:ffff:ffff:ffff:ffff\""
}
```

Mandatory parameters:
- api
- method
- version
- name - Name of the network
- disable_masquerade - Disable IP Masquerade (default: false)

Optional parameters:
- subnet - IPv4 subnet in CIDR notation (e.g.,if not set, it will be generated automatically)
- iprange - IPv4 IP range in CIDR notation (e.g.,if not set, it will be generated automatically)
- gateway - IPv4 gateway address (e.g., if not set, it will be generated automatically)
- enable_ipv6 - Enable IPv6 support (default: false)
- ipv6_subnet - IPv6 subnet in CIDR notation (e.g., 2001:db8:abcd:0012::/64)
- ipv6_iprange - IPv6 IP range in CIDR notation (e.g., 2001:db8:abcd:12::1/64)
- ipv6_gateway - IPv6 gateway address (e.g., 2001:db8:abcd:12:ffff:ffff:ffff:ffff)

### SYNO.Docker.Project

This API provides access to the project management of Container Manager. You can create, delete, and manage projects for your containers.

#### list

List of networks.

- Request method: POST
- Request Body query parameters:

```json 
{
  "api": "SYNO.Docker.Project",
  "method": "list",
  "version": "1"
}
```

#### get

Get project details.

- Request method: POST
- Request Body query parameters:

```json 
{
  "api": "SYNO.Docker.Project",
  "method": "get",
  "version": "1",
  "id": "id-of-project"
}
```