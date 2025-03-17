# List Operating Systems

This request lists operating systems in the region.

## **GET /operating_systems**

### **Request**

#### **Query Parameters**

| Parameter  | Required | Type   | Description |
|------------|----------|--------|-------------|
| `version`  | ✅ | string | The API version, in format YYYY-MM-DD. Specify any date between 2024-11-19 and 2025-03-11. |
| **Possible values** | | | Length = 10, must match regex: `^\d{4}-(0[1-9]|1[0-2])-(0[1-9]|[12]\d|3[01])$` |
| **Example** | | | `2024-06-23` |
| `generation`  | ✅ | int32  | The infrastructure generation. Specify `2`. |
| **Allowable values** | | | `[2]` |
| `start`  | ❌ | string | A server-provided token determining what resource to start the page on. |
| **Possible values** | | | Length: `1 ≤ length ≤ 4096`, regex: `^[ -~]+$` |
| `limit`  | ❌ | int32  | The number of resources to return on a page. |
| **Possible values** | | | `1 ≤ value ≤ 100` |
| **Default** | | | `50` |

### **Example Request**
```sh
curl -X GET "$vpc_api_endpoint/v1/operating_systems?version=2025-03-11&generation=2" \
     -H "Authorization: Bearer $iam_token"
```

---

## **Response**

### **Response Body**

#### **OperatingSystemCollection**

| Field | Required | Type | Description |
|--------|----------|------|-------------|
| `first`  | ✅ | PageLink | A link to the first page of resources. |
| `limit`  | ✅ | int32 | The maximum number of resources returned by the request. |
| **Possible values** | | | `1 ≤ value ≤ 100` |
| **Example** | | | `20` |
| `operating_systems` | ✅ | OperatingSystem[] | A list of operating systems. |
| `total_count` | ✅ | int32 | The total number of resources across all pages. |
| **Possible values** | | | `value ≥ 0` |
| **Example** | | | `132` |
| `next`  | ❌ | PageLink | A link to the next page of resources (not present on the last page). |

### **Status Codes**

| Code | Description |
|------|-------------|
| 200  | The operating systems were retrieved successfully. |

---

### **Example Response**

#### **Status 200**

```json
{
  "first": {
    "href": "https://us-south.iaas.cloud.ibm.com/v1/operating_systems?limit=20"
  },
  "limit": 20,
  "operating_systems": [
    {
      "allow_user_image_creation": true,
      "architecture": "amd64",
      "dedicated_host_only": false,
      "display_name": "Ubuntu Linux 24.04 LTS Noble Numbat Minimal Install (amd64)",
      "family": "Ubuntu Linux",
      "href": "https://us-south.iaas.cloud.ibm.com/v1/operating_systems/ubuntu-24-04-amd64",
      "name": "ubuntu-24-04-amd64",
      "user_data_format": "cloud_init",
      "vendor": "Canonical",
      "version": "24.04 LTS Noble Numbat Minimal Install"
    },
    {
      "allow_user_image_creation": true,
      "architecture": "amd64",
      "dedicated_host_only": false,
      "display_name": "Debian GNU/Linux 8.x jessie/Stable - Minimal Install (amd64)",
      "family": "Debian GNU/Linux",
      "href": "https://us-south.iaas.cloud.ibm.com/v1/operating_systems/debian-8-amd64",
      "name": "debian-8-amd64",
      "user_data_format": "cloud_init",
      "vendor": "Debian",
      "version": "8.x jessie/Stable - Minimal Install"
    },
    {
      "allow_user_image_creation": true,
      "architecture": "amd64",
      "dedicated_host_only": false,
      "display_name": "Debian GNU/Linux 9.x Stretch/Stable - Minimal Install (amd64)",
      "family": "Debian GNU/Linux",
      "href": "https://us-south.iaas.cloud.ibm.com/v1/operating_systems/debian-9-amd64",
      "name": "debian-9-amd64",
      "user_data_format": "cloud_init",
      "vendor": "Debian",
      "version": "9.x Stretch/Stable - Minimal Install"
    },
    {
      "allow_user_image_creation": true,
      "architecture": "amd64",
      "dedicated_host_only": false,
      "display_name": "Red Hat Enterprise Linux 7.x - Minimal Install (amd64)",
      "family": "Red Hat Enterprise Linux",
      "href": "https://us-south.iaas.cloud.ibm.com/v1/operating_systems/red-7-amd64",
      "name": "red-7-amd64",
      "user_data_format": "cloud_init",
      "vendor": "Red Hat",
      "version": "7.x - Minimal Install"
    }
  ],
  "total_count": 4
}

```
