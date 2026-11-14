# Lab - JSON and API Exercise

> **Core CCNA concept exercise** · **Platform:** any text editor and optional Python 3 · **No live controller required.**

## Objective
Read a structured device inventory record and understand HTTP methods without needing Cisco hardware.

## Step 1 — Create `device.json`
```json
{
  "hostname": "R1",
  "interfaces": [
    {"name": "GigabitEthernet0/0", "ip": "192.0.2.1", "up": true},
    {"name": "GigabitEthernet0/1", "ip": null, "up": false}
  ]
}
```

## Step 2 — Validate and inspect
```bash
python3 -m json.tool device.json
python3 -c "import json; d=json.load(open('device.json')); print(d['interfaces'][0]['ip'])"
```

## Step 3 — Interpret hypothetical API requests
```http
GET /api/v1/devices/R1 HTTP/1.1
Authorization: Bearer <token>

PATCH /api/v1/devices/R1 HTTP/1.1
Content-Type: application/json
```

The endpoints above are **illustrative**, not a working Cisco API server.

## Verification
The Python command prints `192.0.2.1`. Identify the array/object/string/boolean/null values. Explain the difference between GET and PATCH.

## Troubleshoot
Ensure JSON uses double quotes, commas between elements and lowercase `true`/`false`/`null`.

## Lesson learned
APIs expose resources and JSON represents structured data; neither requires manually typing configuration commands line by line.

---
[← Previous: 03 - REST APIs and JSON](03%20-%20REST%20APIs%20and%20JSON.md) · [Next: 05 - Ansible and Terraform →](05%20-%20Ansible%20and%20Terraform.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
