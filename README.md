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