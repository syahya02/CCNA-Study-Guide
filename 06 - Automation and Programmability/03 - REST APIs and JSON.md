# REST APIs and JSON

## REST essentials
A REST-style API exchanges resources using HTTP. Common verbs: `GET` read, `POST` create, `PUT` replace, `PATCH` update, `DELETE` remove. Read the API's actual contract before assuming methods are supported.

| Response code | Typical meaning |
|---:|---|
| 200 | Successful request |
| 201 | Resource created |
| 204 | Success, no response body |
| 400 | Invalid request |
| 401 | Not authenticated |
| 403 | Not authorised |
| 404 | Not found |

**Authentication** may use bearer tokens or API keys. Use TLS (HTTPS), protect credentials and validate responses.

## JSON structure
```json
{
  "hostname": "SW1",
  "enabled": true,
  "vlans": [10, 20],
  "management": {"address": "192.0.2.10", "prefix": 24}
}
```

`{}` is an object, `[]` an array; values can be strings, numbers, booleans and `null`. JSON keys and string values use double quotes.

## Practise this topic

- [Lab - JSON and API Exercise](04%20-%20Lab%20-%20JSON%20and%20API%20Exercise.md)

---
[← Previous: 02 - Controllers and SDN Architecture](02%20-%20Controllers%20and%20SDN%20Architecture.md) · [Next: 04 - Lab - JSON and API Exercise →](04%20-%20Lab%20-%20JSON%20and%20API%20Exercise.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
