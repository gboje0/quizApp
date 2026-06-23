
# MyFoundry Data API - User Guide

## Overview

The MyFoundry Data API provides access to financial wellbeing data across geographic regions in the UK. The API offers insights into: 

- Overdrawn accounts
- Low emergency resilience
- Living beyond means indicators.

All data can be filtered by geographic level, time periods, demographics, and spatial boundaries.

## Base URL

```http
https://economic-wellbeing-explorer.services.smartdatafoundry.com
```

## Authentication

The API uses API key authentication. All requests require a valid API key in the `X-MyFoundry-User-Api-Key` header. API keys can be generated in the settings section of the MyFoundry platform. [2]

```bash
X-MyFoundry-User-Api-Key: <your API key>
```

## Available Endpoints

### 1. Overdrawn Accounts

Retrieve data about overdrawn accounts across geographic areas.

**Endpoint**
```http
GET /overdrawn-accounts
```

**Example**
```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts?geographicLevel=itl1&date=2023-01-01" -H "X-MyFoundry-User-Api-Key: <your API key>"
```

### 2. Low Emergency Resilience

Access low emergency resilience metrics.

**Endpoint**
```http
GET /emergency-resilience
```

**Example**
```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/emergency-resilience?geographicLevel=la&dateRange=2023-01-01:2023-12-31" -H "X-MyFoundry-User-Api-Key: <your API key>"
```

### 3. Living Beyond Means

Query data about individuals living beyond their means.

**Endpoint**
```http
GET /living-beyond-means
```

**Example**
```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/living-beyond-means?areas=E12000001,E12000002" -H "X-MyFoundry-User-Api-Key: <your API key>"
```

## Query Parameters

All endpoints support optional query parameters for geographic, temporal, demographic, and pagination filtering. 

### Geographic Filtering

| Parameter | Type | Description | Example |
|---|---|---|---|
| `geographicLevel` | string | Geographic level. Supported values include `itl1`, `itl2`, `iz`, and `la`. | `itl1` |
| `areas` | string | Comma-separated list of area IDs. | `E12000001,E12000002` |
| `boundingBox` | string | Spatial filter in the format `minLng,minLat,maxLng,maxLat`. | `-3.21344,55.94535,-3.15828,55.96247` |

**Note**
| Level| Example |
|---|---|
| ITL1 | Scotland, Wales, regions of England |
| ITL2 | Eastern Scotland, North East England |
| LA (Local Authority) | Council areas |
| IZ (Intermediate Zone / MSOA) | sub-LA |

### Temporal Filtering

| Parameter | Type | Description | Example |
|---|---|---|---|
| `date` | string | Single date in `YYYY-MM-DD` format. Cannot be used with `dateRange`. | `2023-01-01` |
| `dateRange` | string | Date range in `YYYY-MM-DD:YYYY-MM-DD` format. Cannot be used with `date`. | `2023-01-01:2023-12-31` |

**Note:** You can use either `date` or `dateRange`, but not both.

### Demographic Filtering

| Parameter | Type | Description | Example |
|---|---|---|---|
| `ageBand` | string | Age band filter. Supported values include `18-25`, `26-35`, `36-50`, `51-65`, `65+`, and `all`. | `18-25` |
| `incomeBand` | string | Income band filter. Use a specific income band value (`<24k`, `24k - 39999`, `40k+` or `all`. | `all` |

### Pagination

| Parameter | Type | Description | Default | Constraints |
|---|---|---|---|---|
| `page` | number | Page number. | `1` | Minimum: `1` |
| `size` | number | Results per page. | `10000` | Minimum: `1`, maximum: `10000` |

## Response Structure

All successful responses return a `200 OK` status and follow this general structure.

```json
{
  "data": [
    {
      "id": "string",
      "geom": [number, number],
      "name": "string",
      "itl1Id": "string",
      "itl2Id": "string",
      "localAuthorityId": "string",
      "date": "string",
      "ageBand": "string",
      "incomeBand": "string",
      "overdraft": number
    }
  ],
  "metadata": {
    "totalResults": 1000,
    "totalPages": 10,
    "page": 1,
    "size": 100,
    "first": "https://...",
    "last": "https://...",
    "next": "https://...",
    "previous": "https://..."
  }
}
```
## Response Fields

### Data Object Fields
- **id**: Unique identifier for the record
- **geom**: Geometry coordinates [longitude, latitude]
- **name**: Geographic area name
- **itl1Id**: ITL1 region identifier
- **itl2Id**: ITL2 region identifier
- **localAuthorityId**Local authority identifier
- **date**: Date of the data point
- **ageBand**: Age band category
- **incomeBand**: Income band category
- **Metric field**: The specific metric varies by endpoint (overdraft, emergencyResilience, beyondMeans)

### Metadata Object
- **totalResults**: Total number of results across all pages
- **totalPages**: Total number of pages available
- **page**: Current page number
- **size**: Number of results per page
- **first**: URL to the first page
- **last**: URL to the last page
- **next**: URL to the next page (null if on last page)
- **previous**: URL to the previous page (null if on first page)

## Error Codes

| Code | Description | Meaning |
|---|---|---|
| `401` | Unauthorized | Missing or invalid API key. |
| `403` | Forbidden | Insufficient permissions. |
| `404` | Not Found | Endpoint not found. |
| `405` | Method Not Allowed | HTTP method not supported. |
| `409` | Conflict | Request conflicts with current state. |
| `500` | Internal Server Error | Server error. |
| `501` | Bad Gateway | Gateway error. |
| `503` | Service Unavailable | Service temporarily unavailable. |

## Usage Examples

### Example 1: Get Latest Data for All ITL1 Regions

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts?geographicLevel=itl1" -H "X-MyFoundry-User-Api-Key: <your API key>"
```

### Example 2: Filter by Specific Areas and Date Range

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/emergency-resilience?areas=E12000001,E12000002&dateRange=2023-01-01:2023-12-31" -H "X-MyFoundry-User-Api-Key: <your API key>"
```

### Example 3: Filter by Demographics

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/living-beyond-means?ageBand=26-35&incomeBand=a" -H "X-MyFoundry-User-Api-Key: <your API key>"
```

### Example 4: Use Bounding Box for Spatial Filtering

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts?boundingBox=-3.21344,55.94535,-3.15828,55.96247" -H "X-MyFoundry-User-Api-Key: <your API key>"
```

### Example 5: Paginated Request

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/emergency-resilience?page=2&size=50" -H "X-MyFoundry-User-Api-Key: <your API key>"
```
### Pagination Best Practices

- **Start with page 1** and use the metadata.next URL to navigate to subsequent pages
- **Check metadata.totalPages** to determine how many pages are available
- **Use reasonable page sizes** (default is 10000, but smaller sizes may improve performance)
- **Handle empty results** - A 204 status code indicates no data matches your criteria

Example pagination flow:

```py
import requests

base_url = "https://myfoundry-data-api.dev.services.smartdatafoundry.com"
headers = {"Authorization": f"Bearer {token}"}
all_data = []

# Start with page 1
response = requests.get(f"{base_url}/overdrawn-accounts?page=1&size=100", headers=headers)
result = response.json()

all_data.extend(result['data'])

# Continue while there's a next page
while result['metadata'].get('next'):
    response = requests.get(result['metadata']['next'], headers=headers)
    result = response.json()
    all_data.extend(result['data'])

print(f"Retrieved {len(all_data)} total records")
```
## Parameter Validation Rules

### Date Formats
- **Single date:**  `YYYY-MM-DD` (e.g., `2023-01-01`)
- **Date range:** `YYYY-MM-DD:YYYY-MM-DD` (e.g., `2023-01-01:2023-12-31`)

### Geographic Levels
Valid values: `itl1`, `itl2`, `iz`, `la`

### Age Bands
Valid values: `18-25`, `26-35`, `36-50`, `51-65`, `65+`, `all`

### Bounding Box Format
Format: `minLongitude,minLatitude,maxLongitude,maxLatitude`

Example: `-3.21344,55.94535,-3.15828,55.96247`

## Tips and Best Practices
1. **Handle rate limiting** - Implement exponential backoff if you receive 429 responses
2. **Use appropriate page sizes** - Smaller page sizes (100-1000) provide better response times
3. **Filter data at the API level** - Use query parameters rather than fetching all data and filtering client-side
4. **Check for 204 responses** - Empty results return 204 No Content, not 200 with empty array
5. **Use the correlationId** - Include this in any support requests for faster troubleshooting
6. **Validate parameters** - The API validates all parameters; invalid requests return 400 with details
7. **Respect CORS policies** - The API allows GET and OPTIONS methods from any origin
