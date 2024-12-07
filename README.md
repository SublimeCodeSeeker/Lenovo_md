`# Lenovo API points Documentation

## Overview
The AHU Points API provides access to various points within an Air Handler Unit (AHU). Users can retrieve data for specific points by providing the corresponding point tag. Each AHU is accessible through an endpoint format `/UMAXX`, where `XX` represents the AHU number.

## Authentication
This API uses Basic Authentication, requiring a username and password for access.

- **Username**: apiuser
- **Password**: Admin12345

Include the Base64 encoded credentials in the request header as shown below:

Authorization: Basic <Base64(username)>

## Endpoints

### Get Points for AHU

- **Endpoint**: `/UMAXX`
- **Method**: `GET`
- **Description**: Retrieves data for a specific point in the AHU by providing the point tag.
- **Parameters**:
  - `point`: (Required) The tag of the point to retrieve. Use a tag from the table below.
- **Response**:
  - `200 OK`: Returns the data for the requested point.
  - `400 Bad Request`: Missing or invalid point tag.
  - `401 Unauthorized`: Invalid authentication credentials.

#### Example Request
```http
GET /UMAXX?point=<point_tag> HTTP/1.1
Host: 10.196.122.154
Port: 443 (HTTPS)
Authorization: Basic <Base64(username:password)>
```

**note** : until now the AHU (Air Handlers Units) go up to 24.```````

### List of AHU (UMA) 

| Point Tag      | Description       |
|----------------|-------------------|
| `UMA01`    | Air Handler Unit 01   |
| `UMA02`    | Air Handler Unit 02   |
| `UMA03`    | Air Handler Unit 03   |
| `UMA04`    | Air Handler Unit 04   |
| `UMA05`    | Air Handler Unit 05   |
| `UMA06`    | Air Handler Unit 06   |
| `UMA07`    | Air Handler Unit 07   |
| `UMA08`    | Air Handler Unit 08   |
| `UMA09`    | Air Handler Unit 09   |
| `UMA10`    | Air Handler Unit 10   |
| `UMA11`    | Air Handler Unit 11   |
| `UMA12`    | Air Handler Unit 12   |
| `UMA13`    | Air Handler Unit 13   |
| `UMA14`    | Air Handler Unit 14   |
| `UMA15`    | Air Handler Unit 15   |
| `UMA16`    | Air Handler Unit 16   |
| `UMA17`    | Air Handler Unit 17   |
| `UMA18`    | Air Handler Unit 18   |
| `UMA19`    | Air Handler Unit 19   |
| `UMA20`    | Air Handler Unit 20   |
| `UMA21`    | Air Handler Unit 21   |
| `UMA22`    | Air Handler Unit 22   |
| `UMA23`    | Air Handler Unit 23   |
| `UMA24`    | Air Handler Unit 24   |

### Points List AHU 01-03 and 09-14

The following table provides a list of valid points that can be used as point parameters in the GET request for AHU 01 to 03 and AHU 09 to 14.

| Point Tag      | Description                   |
|----------------|-------------------------------|
| `AD_AE_POS`    | Exhaust Air Damper Position   |
| `AD_AR_POS`    | Return Air Damper Position    |
| `CLG-O`        | Cooling Valve                 |
| `CLG-POS`      | Cooling Valve Position        |
| `EFFCLG-SP`    | Effective Cooling Setpoint    |
| `SF-A`         | Supply Fan Alarm              |
| `SF-C`         | Supply Fan Command            |
| `SF-O`         | Supply Fan Output             |
| `SF-S`         | Supply Fan Status             |
| `ST-CM`        | Temperature Mixed Box         |
| `STR`          | Temperature Return            |
| `STS`          | Temperature Supply            |
| `TDP-1`        | Differential Pressure Filter 1|
| `TDP-3`        | Differential Pressure Filter 2|                              
| `UNITEN-MODE`  | Enable Unit                   |
| `ZN-H`         | Zone Humidity                 |
| `ZN-T`         | Zone Temperature              |


Note 1: Replace <point_tag> with one of the tags listed above when making a request.

### Points List AHU 04-08 and 15-24

The following table provides a list of valid points that can be used as point parameters in the GET request for AHU 04 to 08 and AHU 15 to 24.

| Point Tag      | Description                   |
|----------------|-------------------------------|
| `CLG-O`        | Cooling Valve                 |
| `EFFCLG-SP`    | Effective Cooling Setpoint    |
| `SF-A`         | Supply Fan Alarm              |
| `SF-C`         | Supply Fan Command            |
| `SF-O`         | Supply Fan Output             |
| `SF-S`         | Supply Fan Status             |
| `ST-CM`        | Temperature Mixed Box         |
| `STR`          | Temperature Return            |
| `STS`          | Temperature Supply            |
| `TDP-1`        | Differential Pressure Filter 1|
| `TDP-3`        | Differential Pressure Filter 2|                              
| `UNITEN-MODE`  | Enable Unit                   |
| `ZN-H`         | Zone Humidity                 |
| `ZN-T`         | Zone Temperature              |


Note 1: Replace <point_tag> with one of the tags listed above when making a request.

### Sample Response

Below is a sample response body for a successful read request, along with descriptions of each field:


```json
{
    "timestamp": "2024-12-03 13:02:57.937-0800",
    "EFFCLG-SP": {
        "status": "{ok}",
        "Out": 25
    }
}
```



| Field           | Type      | Description                                                                                     |
|-----------------|-----------|-------------------------------------------------------------------------------------------------|
| ├ `timestamp`   | `string`  | Timestamp of the data point in ISO 8601 format with timezone offset.                            |
| ├ `pointName`   | `string`  | Name of the point/variable being read                                                           |
| ├ `status`      | `string`  | Current status of the data point, such as operational indicators (e.g., `{down,stale}`).        |
| └ `out `        | `integer` | Numerical value of the requested point (e.g., temperature, airflow), specific to the point tag. |


### Error Codes

| Code | Description                              |
|------|------------------------------------------|
| 400  | Bad Request – Invalid point tag provided |
| 401  | Unauthorized – Authentication required   |
| 404  | Not Found – AHU or point not available   |

