
                        <!DOCTYPE html>
                        <html lang="en">
                        <head>
                            <meta charset="UTF-8">
                            <meta name="viewport" content="width=device-width, initial-scale=1.0">
							<style>
								body {
									background-color: white; /* Ensure the iframe has a white background */
								}

								
							</style>
                        </head>
                        <body>
                            <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>MyFoundry Data API - User Guide</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      margin: 40px;
      color: #222;
      max-width: 100%;
      box-sizing: border-box;
    }

    h1, h2, h3 {
      color: #1f4e79;
    }

    code {
      background: #f4f4f4;
      padding: 2px 5px;
      border-radius: 4px;
      font-family: Consolas, monospace;
      white-space: normal;
      overflow-wrap: anywhere;
      word-break: break-word;
    }

    pre {
      background: #f4f4f4;
      padding: 12px;
      border-radius: 4px;
      border: 1px solid #ddd;
      font-family: Consolas, monospace;

      /* Keeps example requests inside the page */
      white-space: pre-wrap;
      overflow-wrap: anywhere;
      word-break: break-word;
      max-width: 100%;
      box-sizing: border-box;
      overflow-x: hidden;
    }

    pre code {
      white-space: pre-wrap;
      overflow-wrap: anywhere;
      word-break: break-word;
      display: block;
    }

    table {
      border-collapse: collapse;
      width: 100%;
      margin: 20px 0;
      table-layout: fixed;
      word-wrap: break-word;
    }

    th, td {
      border: 1px solid #ccc;
      padding: 8px;
      text-align: left;
      vertical-align: top;
      overflow-wrap: anywhere;
      word-break: break-word;
    }

    th {
      background: #e8f1fa;
    }

    .note {
      background: #fff8dc;
      border-left: 4px solid #f0ad4e;
      padding: 10px;
      margin: 15px 0;
    }

    @media print {
      body {
        margin: 20mm;
      }

      pre, code, table {
        page-break-inside: avoid;
        break-inside: avoid;
      }

      pre {
        white-space: pre-wrap;
        overflow-wrap: anywhere;
        word-break: break-word;
      }
    }
  </style>
</head>

<body>

  <h1>MyFoundry Data API - User Guide</h1>

  <h2>Overview</h2>
  <p>
    The MyFoundry Data API provides access to financial wellbeing data across geographic regions in the UK.
  </p>

  <p>The API offers insights into:</p>
  <ul>
    <li>Overdrawn accounts</li>
    <li>Emergency financial resilience</li>
    <li>Living beyond means indicators</li>
  </ul>

  <p>
    All data can be filtered by geographic level, time periods, demographics, and spatial boundaries.
  </p>

  <h2>Base URL</h2>
  <p>
    <code>https://economic-wellbeing-explorer.services.smartdatafoundry.com</code>
  </p>

  <h2>Authentication</h2>
  <p>
    The MyFoundry data API uses API key authentication. All requests require a valid API key in the
    <code>X-MyFoundry-User-Api-Key</code> header:
  </p>

  <pre><code>X-MyFoundry-User-Api-Key: &lt;your API key&gt;</code></pre>

  <p>
    API keys can be generated in the settings section of the MyFoundry platform.
  </p>

  <h2>Available Endpoints</h2>

  <h3>1. Overdrawn Accounts</h3>
  <p>
    Retrieve data about overdrawn accounts across geographic areas.
  </p>

  <p><strong>Endpoint:</strong></p>
  <pre><code>GET /overdrawn-accounts</code></pre>

  <p><strong>Example Request:</strong></p>
  <pre><code>curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts?geographicLevel=itl1&amp;date=2023-01-01" \
-H "X-MyFoundry-User-Api-Key: &lt;your API key&gt;"</code></pre>

  <h3>2. Emergency Resilience</h3>
  <p>
    Access emergency financial resilience metrics.
  </p>

  <p><strong>Endpoint:</strong></p>
  <pre><code>GET /emergency-resilience</code></pre>

  <p><strong>Example Request:</strong></p>
  <pre><code>curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/emergency-resilience?geographicLevel=la&amp;dateRange=2023-01-01:2023-12-31" \
-H "X-MyFoundry-User-Api-Key: &lt;your API key&gt;"</code></pre>

  <h3>3. Living Beyond Means</h3>
  <p>
    Query data about individuals living beyond their means.
  </p>

  <p><strong>Endpoint:</strong></p>
  <pre><code>GET /living-beyond-means</code></pre>

  <p><strong>Example Request:</strong></p>
  <pre><code>curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/living-beyond-means?areas=E12000001,E12000002" \
-H "X-MyFoundry-User-Api-Key: &lt;your API key&gt;"</code></pre>

  <h2>Query Parameters</h2>
  <p>
    All endpoints support optional query parameters for geographic, temporal, demographic, and pagination filtering.
  </p>

  <h3>Geographic Filtering</h3>

  <table>
    <thead>
      <tr>
        <th>Parameter</th>
        <th>Type</th>
        <th>Description</th>
        <th>Example</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>geographicLevel</code></td>
        <td>string</td>
        <td>Geographic level. Supported values include <code>itl1</code>, <code>itl2</code>, <code>itl3</code>, and <code>la</code>.</td>
        <td><code>itl1</code></td>
      </tr>
      <tr>
        <td><code>areas</code></td>
        <td>string</td>
        <td>Comma-separated list of area IDs.</td>
        <td><code>E12000001,E12000002</code></td>
      </tr>
      <tr>
        <td><code>boundingBox</code></td>
        <td>string</td>
        <td>Spatial filter in the format <code>minLng,minLat,maxLng,maxLat</code>.</td>
        <td><code>-3.21344,55.94535,-3.15828,55.96247</code></td>
      </tr>
    </tbody>
  </table>

  <h3>Temporal Filtering</h3>

  <table>
    <thead>
      <tr>
        <th>Parameter</th>
        <th>Type</th>
        <th>Description</th>
        <th>Example</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>date</code></td>
        <td>string</td>
        <td>Single date in <code>YYYY-MM-DD</code> format. Cannot be used with <code>dateRange</code>.</td>
        <td><code>2023-01-01</code></td>
      </tr>
      <tr>
        <td><code>dateRange</code></td>
        <td>string</td>
        <td>Date range in <code>YYYY-MM-DD:YYYY-MM-DD</code> format. Cannot be used with <code>date</code>.</td>
        <td><code>2023-01-01:2023-12-31</code></td>
      </tr>
    </tbody>
  </table>

  <div class="note">
    <strong>Note:</strong> You can use either <code>date</code> or <code>dateRange</code>, but not both.
  </div>

  <h3>Demographic Filtering</h3>

  <table>
    <thead>
      <tr>
        <th>Parameter</th>
        <th>Type</th>
        <th>Description</th>
        <th>Example</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>ageBand</code></td>
        <td>string</td>
        <td>Age band filter. Supported values include <code>18-25</code>, <code>26-35</code>, <code>36-50</code>, <code>51-65</code>, <code>65+</code>, and <code>all</code>.</td>
        <td><code>18-25</code></td>
      </tr>
      <tr>
        <td><code>incomeBand</code></td>
        <td>string</td>
        <td>Income band filter. Use a specific income band value or <code>all</code>.</td>
        <td><code>all</code></td>
      </tr>
    </tbody>
  </table>

  <h3>Pagination</h3>

  <table>
    <thead>
      <tr>
        <th>Parameter</th>
        <th>Type</th>
        <th>Description</th>
        <th>Default</th>
        <th>Constraints</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>page</code></td>
        <td>number</td>
        <td>Page number.</td>
        <td><code>1</code></td>
        <td>Minimum: <code>1</code></td>
      </tr>
      <tr>
        <td><code>size</code></td>
        <td>number</td>
        <td>Results per page.</td>
        <td><code>10000</code></td>
        <td>Minimum: <code>1</code>, maximum: <code>10000</code></td>
      </tr>
    </tbody>
  </table>

  <h2>Response Structure</h2>
  <p>
    All successful responses return a <code>200 OK</code> status and follow this general structure:
  </p>

  <pre><code>{
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
}</code></pre>

  <h2>Error Codes</h2>

  <table>
    <thead>
      <tr>
        <th>Code</th>
        <th>Description</th>
        <th>Meaning</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>401</code></td>
        <td>Unauthorized</td>
        <td>Missing or invalid API key.</td>
      </tr>
      <tr>
        <td><code>403</code></td>
        <td>Forbidden</td>
        <td>Insufficient permissions.</td>
      </tr>
      <tr>
        <td><code>404</code></td>
        <td>Not Found</td>
        <td>Endpoint not found.</td>
      </tr>
      <tr>
        <td><code>405</code></td>
        <td>Method Not Allowed</td>
        <td>HTTP method not supported.</td>
      </tr>
      <tr>
        <td><code>409</code></td>
        <td>Conflict</td>
        <td>Request conflicts with current state.</td>
      </tr>
      <tr>
        <td><code>500</code></td>
        <td>Internal Server Error</td>
        <td>Server error.</td>
      </tr>
      <tr>
        <td><code>501</code></td>
        <td>Bad Gateway</td>
        <td>Gateway error.</td>
      </tr>
      <tr>
        <td><code>503</code></td>
        <td>Service Unavailable</td>
        <td>Service temporarily unavailable.</td>
      </tr>
    </tbody>
  </table>

  <h2>Usage Examples</h2>

  <h3>Example 1: Get Latest Data for All ITL1 Regions</h3>
  <pre><code>curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts?geographicLevel=itl1" \
-H "X-MyFoundry-User-Api-Key: &lt;your API key&gt;"</code></pre>

  <h3>Example 2: Filter by Specific Areas and Date Range</h3>
  <pre><code>curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/emergency-resilience?areas=E12000001,E12000002&amp;dateRange=2023-01-01:2023-12-31" \
-H "X-MyFoundry-User-Api-Key: &lt;your API key&gt;"</code></pre>

  <h3>Example 3: Filter by Demographics</h3>
  <pre><code>curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/living-beyond-means?ageBand=26-35&amp;incomeBand=a" \
-H "X-MyFoundry-User-Api-Key: &lt;your API key&gt;"</code></pre>

  <h3>Example 4: Use Bounding Box for Spatial Filtering</h3>
  <pre><code>curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts?boundingBox=-3.21344,55.94535,-3.15828,55.96247" \
-H "X-MyFoundry-User-Api-Key: &lt;your API key&gt;"</code></pre>

  <h3>Example 5: Paginated Request</h3>
  <pre><code>curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/emergency-resilience?page=2&amp;size=50" \
-H "X-MyFoundry-User-Api-Key: &lt;your API key&gt;"</code></pre>

</body>
</html>

							<script>
                            	
							</script>
                        </body>
                        </html>
                    
