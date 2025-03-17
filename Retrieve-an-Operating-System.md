# Retrieve an Operating System

This request retrieves a single operating system specified by the name in the URL.

## **GET /operating_systems/{name}**

### **Request**

#### **Path Parameters**
| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `name` | ✅ | string | The operating system name |

- **Possible values:** 1 ≤ length ≤ 63, matches regex: `^([a-z]|[a-z][-a-z0-9]*[a-z0-9]|[0-9][-a-z0-9]*([a-z]|[-a-z][-a-z0-9]*[a-z0-9]))$`
- **Example:** `red-7-amd64`

#### **Query Parameters**
| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `version` | ✅ | string | The API version, in format YYYY-MM-DD. Valid between `2024-11-19` and `2025-03-11` |
| `generation` | ✅ | int32 | The infrastructure generation. Allowed value: `2` |

- **Possible values for `version`**: `length = 10`, matches regex: `^\d{4}-(0[1-9]|1[0-2])-(0[1-9]|[12]\d|3[01])$`
- **Example `version`**: `2024-06-23`
- **Example `generation`**: `2`

### **Example Request**
```sh
curl -X GET "$vpc_api_endpoint/v1/operating_system/$operating_system_name?version=2025-03-11&generation=2" \
  -H "Authorization: Bearer $iam_token"
```

---

## **Response**

### **Response Body: OperatingSystem**

| Field | Included | Type | Description |
|--------|----------|------|-------------|
| `allow_user_image_creation` | ✅ | boolean | Users may create new images with this operating system |
| `architecture` | ✅ | string | The operating system architecture |
| `dedicated_host_only` | ✅ | boolean | Whether the OS can only be used on dedicated hosts |
| `display_name` | ✅ | string | A unique, display-friendly name for the OS |
| `family` | ✅ | string | The software family for this OS |
| `href` | ✅ | string | The URL for this OS |
| `name` | ✅ | string | The globally unique name for this OS |
| `user_data_format` | ✅ | string | The user data format for this OS |
| `vendor` | ✅ | string | The OS vendor |
| `version` | ✅ | string | The major release version of this OS |

### **Example Response (200)**
```json
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
}
```

### **Status Codes**
| Code | Description |
|------|-------------|
| `200` | The operating system was retrieved successfully. |
| `404` | An operating system with the specified name could not be found. |

---

