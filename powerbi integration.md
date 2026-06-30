
# Using the MyFoundry Production Data API with Power BI

A step-by-step guide for connecting Power BI Desktop to the MyFoundry production API using API key authentication.

---

## 1. Understand the Production API

The MyFoundry production API provides access to economic and financial wellbeing data. The production base URL used in the API examples is:

```text
https://economic-wellbeing-explorer.services.smartdatafoundry.com

```

Example endpoints include:

* `/overdrawn-accounts`
* `/emergency-resilience`
* `/living-beyond-means`

The API supports optional query parameters for geographic, temporal, demographic, and pagination filtering.

---

## 2. Authentication

The production API uses an API key header. Each request should include:

```text
X-MyFoundry-User-Api-Key: YOUR_API_KEY

```

The API documentation examples use the `X-MyFoundry-User-Api-Key` header for authentication.

> **Important:** Do not share your API key publicly. Avoid placing it in screenshots, public repositories, unsecured documents, or shared PBIX files.

---

## 3. Available Production Endpoints

| Dataset | Endpoint | Example Purpose |
| --- | --- | --- |
| Overdrawn Accounts | `/overdrawn-accounts` | Retrieve overdrawn account data by geographic area. |
| Emergency Resilience | `/emergency-resilience` | Retrieve emergency financial resilience data. |
| Living Beyond Means | `/living-beyond-means` | Retrieve living beyond means data. |

Example full endpoint:

```text
https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts

```

---

## 4. Example API Requests

### Example 1: Get Latest Data for All ITL1 Regions

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts?geographicLevel=itl1" \
-H "X-MyFoundry-User-Api-Key: YOUR_API_KEY"

```

### Example 2: Filter by Specific Areas and Date Range

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/emergency-resilience?areas=E12000001,E12000002&dateRange=2023-01-01:2023-12-31" \
-H "X-MyFoundry-User-Api-Key: YOUR_API_KEY"

```

### Example 3: Filter by Demographics

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/living-beyond-means?ageBand=26-35&incomeBand=a" \
-H "X-MyFoundry-User-Api-Key: YOUR_API_KEY"

```

### Example 4: Use Bounding Box for Spatial Filtering

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts?boundingBox=-3.21344,55.94535,-3.15828,55.96247" \
-H "X-MyFoundry-User-Api-Key: YOUR_API_KEY"

```

### Example 5: Paginated Request

```bash
curl -X GET "https://economic-wellbeing-explorer.services.smartdatafoundry.com/emergency-resilience?page=2&size=50" \
-H "X-MyFoundry-User-Api-Key: YOUR_API_KEY"

```

The API documentation includes examples for demographic filtering, bounding box filtering, and pagination.

---

## 5. Connect Power BI Desktop to the API

1. Open **Power BI Desktop**.
2. Select **Home**.
3. Click **Get Data**.
4. Select **Web**.
5. Click **Connect**.
6. Choose **Advanced**.
7. Enter the API URL.
8. Add the API key header.

### URL

```text
https://economic-wellbeing-explorer.services.smartdatafoundry.com/overdrawn-accounts

```

### Headers

| Header Name | Header Value |
| --- | --- |
| `X-MyFoundry-User-Api-Key` | `YOUR_API_KEY` |
| `Accept` | `application/json` |

---

## 6. Recommended Power Query M Starter Code

In Power BI, open **Transform Data**, then open **Advanced Editor**, and use the following starter query.

```powerquery
let
    BaseUrl = "https://economic-wellbeing-explorer.services.smartdatafoundry.com",

    ApiKey = "YOUR_API_KEY",

    Source = Json.Document(
        Web.Contents(
            BaseUrl,
            [
                RelativePath = "overdrawn-accounts",
                Headers = [
                    #"X-MyFoundry-User-Api-Key" = ApiKey,
                    Accept = "application/json"
                ]
            ]
        )
    )
in
    Source

```

> **Tip:** Using `RelativePath` and `Query` is recommended in Power BI because it helps avoid dynamic data source problems when publishing to Power BI Service.

---

## 7. Understand Query Parameters

All endpoints support optional query parameters for geographic, temporal, demographic, and pagination filtering.

### Geographic Filtering

| Parameter | Description | Example |
| --- | --- | --- |
| `geographicLevel` | Geographic level. Supported values include `itl1`, `itl2`, `la`, and `iz`. | `itl1` |
| `areas` | Comma-separated list of area IDs. | `E12000001,E12000002` |
| `boundingBox` | Spatial filter in the format `minLng,minLat,maxLng,maxLat`. | `-3.21344,55.94535,-3.15828,55.96247` |

### Temporal Filtering

| Parameter | Description | Example |
| --- | --- | --- |
| `date` | Single date in `YYYY-MM-DD` format. Cannot be used with `dateRange`. | `2023-01-01` |
| `dateRange` | Date range in `YYYY-MM-DD:YYYY-MM-DD` format. Cannot be used with `date`. | `2023-01-01:2023-12-31` |

> **Important:** You can use either `date` or `dateRange`, but not both in the same request.

### Demographic Filtering

| Parameter | Description | Example |
| --- | --- | --- |
| `ageBand` | Age band filter. Supported values include `18-39`, `40-69`, `70+`, and `all`. | `40-69` |
| `incomeBand` | Income band filter. Use a specific income band value or `all`. | `all` |

### Pagination

| Parameter | Description | Default | Constraints |
| --- | --- | --- | --- |
| `page` | Page number. | `1` | Minimum: `1` |
| `size` | Results per page. | `10000` | Minimum: `1`, maximum: `10000` |

---

## 8. Convert the API Response into a Table

Successful responses return a `200 OK` status and follow a general response structure that includes data and metadata.

```powerquery
let
    BaseUrl = "https://economic-wellbeing-explorer.services.smartdatafoundry.com",

    ApiKey = "YOUR_API_KEY",

    Source = Json.Document(
        Web.Contents(
            BaseUrl,
            [
                RelativePath = "overdrawn-accounts",
                Headers = [
                    #"X-MyFoundry-User-Api-Key" = ApiKey,
                    Accept = "application/json"
                ]
            ]
        )
    ),

    Data = Source[data],

    DataTable = Table.FromRecords(Data)
in
    DataTable

```

---

## 9. Extract Longitude and Latitude

If the response contains a `geom` field as an array, you can extract longitude and latitude for map visuals.

```powerquery
let
    BaseUrl = "https://economic-wellbeing-explorer.services.smartdatafoundry.com",

    ApiKey = "YOUR_API_KEY",

    Source = Json.Document(
        Web.Contents(
            BaseUrl,
            [
                RelativePath = "overdrawn-accounts",
                Headers = [
                    #"X-MyFoundry-User-Api-Key" = ApiKey,
                    Accept = "application/json"
                ]
            ]
        )
    ),

    Data = Source[data],

    DataTable = Table.FromRecords(Data),

    AddedLongitude = Table.AddColumn(
        DataTable,
        "Longitude",
        each try [geom]{0} otherwise null,
        type number
    ),

    AddedLatitude = Table.AddColumn(
        AddedLongitude,
        "Latitude",
        each try [geom]{1} otherwise null,
        type number
    )
in
    AddedLatitude

```

---

## 10. Filter by Date Range, Age Band, and Income Band

This example calls the `/living-beyond-means` endpoint using demographic filters.

```powerquery
let
    BaseUrl = "https://economic-wellbeing-explorer.services.smartdatafoundry.com",

    ApiKey = "YOUR_API_KEY",

    Source = Json.Document(
        Web.Contents(
            BaseUrl,
            [
                RelativePath = "living-beyond-means",
                Query = [
                    ageBand = "26-35",
                    incomeBand = "a"
                ],
                Headers = [
                    #"X-MyFoundry-User-Api-Key" = ApiKey,
                    Accept = "application/json"
                ]
            ]
        )
    )
in
    Source

```

---

## 11. Use Spatial Filtering with Bounding Box

The API supports bounding box filtering using the format `minLng,minLat,maxLng,maxLat`.

```powerquery
let
    BaseUrl = "https://economic-wellbeing-explorer.services.smartdatafoundry.com",

    ApiKey = "YOUR_API_KEY",

    Source = Json.Document(
        Web.Contents(
            BaseUrl,
            [
                RelativePath = "overdrawn-accounts",
                Query = [
                    boundingBox = "-3.21344,55.94535,-3.15828,55.96247"
                ],
                Headers = [
                    #"X-MyFoundry-User-Api-Key" = ApiKey,
                    Accept = "application/json"
                ]
            ]
        )
    )
in
    Source

```

---

## 12. Handle Pagination

Pagination uses `page` and `size`. The maximum supported size is `10000`.

### Create a Function Called GetPage

```powerquery
let
    GetPage = (PageNumber as number) =>
        let
            BaseUrl = "https://economic-wellbeing-explorer.services.smartdatafoundry.com",

            ApiKey = "YOUR_API_KEY",

            Source = Json.Document(
                Web.Contents(
                    BaseUrl,
                    [
                        RelativePath = "overdrawn-accounts",
                        Query = [
                            page = Text.From(PageNumber),
                            size = "10000"
                        ],
                        Headers = [
                            #"X-MyFoundry-User-Api-Key" = ApiKey,
                            Accept = "application/json"
                        ]
                    ]
                )
            )
        in
            Source
in
    GetPage

```

### Combine All Pages

```powerquery
let
    FirstPage = GetPage(1),

    TotalPages = FirstPage[metadata][totalPages],

    PageNumbers = List.Numbers(1, TotalPages),

    Pages = List.Transform(PageNumbers, each GetPage(_)),

    DataLists = List.Transform(Pages, each _[data]),

    CombinedData = List.Combine(DataLists),

    DataTable = Table.FromRecords(CombinedData)
in
    DataTable

```

---

## 13. Create Power BI Parameters

Instead of hardcoding values directly into the query, create parameters in Power BI.

| Parameter Name | Type | Example Value |
| --- | --- | --- |
| `BaseUrl` | Text | `https://economic-wellbeing-explorer.services.smartdatafoundry.com` |
| `ApiKey` | Text | `YOUR_API_KEY` |
| `Endpoint` | Text | `overdrawn-accounts` |
| `GeographicLevel` | Text | `itl1` |
| `AgeBand` | Text | `all` |
| `IncomeBand` | Text | `all` |
| `PageSize` | Number | `10000` |

---

## 14. Build Your Power BI Report

This section explains the full process for turning the production API response into a usable Power BI report. The query below includes a fix for missing columns, such as `ITL1 ID`, by checking whether a column exists before applying a data type.

### Step 14.1: Create the Required Power BI Parameters

1. Open **Transform Data**.
2. Go to **Manage Parameters**.
3. Select **New Parameter**.
4. Create the parameters listed in Section 13.

### Step 14.2: Use This Updated Power Query M Query

> **Fix included:** This version avoids the error `The column 'ITL1 ID' of the table wasn't found` by only applying type changes to columns that exist.

```powerquery
let
    BaseUrlValue = BaseUrl,
    ApiKeyValue = ApiKey,
    EndpointValue = Endpoint,
    GeographicLevelValue = GeographicLevel,
    AgeBandValue = AgeBand,
    IncomeBandValue = IncomeBand,
    PageSizeValue = Text.From(PageSize),

    GetPage = (PageNumber as number) as record =>
        let
            Source = Json.Document(
                Web.Contents(
                    BaseUrlValue,
                    [
                        RelativePath = EndpointValue,
                        Query = [
                            geographicLevel = GeographicLevelValue,
                            ageBand = AgeBandValue,
                            incomeBand = IncomeBandValue,
                            page = Text.From(PageNumber),
                            size = PageSizeValue
                        ],
                        Headers = [
                            #"X-MyFoundry-User-Api-Key" = ApiKeyValue,
                            Accept = "application/json"
                        ]
                    ]
                )
            )
        in
            Source,

    FirstPage = GetPage(1),

    TotalPagesRaw = try FirstPage[metadata][totalPages] otherwise 1,

    TotalPages =
        if TotalPagesRaw = null then
            1
        else
            Number.From(TotalPagesRaw),

    PageNumbers = List.Numbers(1, TotalPages),

    Pages = List.Transform(PageNumbers, each GetPage(_)),

    DataLists = List.Transform(Pages, each try _[data] otherwise {}),

    CombinedData = List.Combine(DataLists),

    RawTable =
        if List.IsEmpty(CombinedData) then
            #table(
                {
                    "id",
                    "geom",
                    "name",
                    "itl1Id",
                    "itl2Id",
                    "localAuthorityId",
                    "date",
                    "ageBand",
                    "incomeBand",
                    "overdraft"
                },
                {}
            )
        else
            Table.FromRecords(CombinedData),

    AddedLongitude = Table.AddColumn(
        RawTable,
        "Longitude",
        each try [geom]{0} otherwise null,
        type number
    ),

    AddedLatitude = Table.AddColumn(
        AddedLongitude,
        "Latitude",
        each try [geom]{1} otherwise null,
        type number
    ),

    RenamedColumns = Table.RenameColumns(
        AddedLatitude,
        {
            {"id", "ID"},
            {"geom", "Geometry"},
            {"name", "Area Name"},
            {"itl1Id", "ITL1 ID"},
            {"itl2Id", "ITL2 ID"},
            {"localAuthorityId", "Local Authority ID"},
            {"date", "Date"},
            {"ageBand", "Age Band"},
            {"incomeBand", "Income Band"},
            {"overdraft", "Overdraft"}
        },
        MissingField.Ignore
    ),

    TypeChanges = {
        {"ID", type text},
        {"Area Name", type text},
        {"ITL1 ID", type text},
        {"ITL2 ID", type text},
        {"Local Authority ID", type text},
        {"Date", type date},
        {"Age Band", type text},
        {"Income Band", type text},
        {"Overdraft", type number},
        {"Longitude", type number},
        {"Latitude", type number}
    },

    ExistingTypeChanges =
        List.Select(
            TypeChanges,
            each List.Contains(Table.ColumnNames(RenamedColumns), _{0})
        ),

    ChangedTypes = Table.TransformColumnTypes(
        RenamedColumns,
        ExistingTypeChanges
    ),

    FilteredCoordinates =
        if List.Contains(Table.ColumnNames(ChangedTypes), "Longitude")
            and List.Contains(Table.ColumnNames(ChangedTypes), "Latitude") then
            Table.SelectRows(
                ChangedTypes,
                each [Longitude] <> null and [Latitude] <> null
            )
        else
            ChangedTypes

in
    FilteredCoordinates

```

### Step 14.3: Non-Parameter Version

If you do not want to create Power BI parameters, use this version instead. Replace `YOUR_API_KEY` with your real API key.

```powerquery
let
    BaseUrlValue = "https://economic-wellbeing-explorer.services.smartdatafoundry.com",
    ApiKeyValue = "YOUR_API_KEY",
    EndpointValue = "overdrawn-accounts",
    GeographicLevelValue = "itl1",
    AgeBandValue = "all",
    IncomeBandValue = "all",
    PageSizeValue = "10000",

    GetPage = (PageNumber as number) as record =>
        let
            Source = Json.Document(
                Web.Contents(
                    BaseUrlValue,
                    [
                        RelativePath = EndpointValue,
                        Query = [
                            geographicLevel = GeographicLevelValue,
                            ageBand = AgeBandValue,
                            incomeBand = IncomeBandValue,
                            page = Text.From(PageNumber),
                            size = PageSizeValue
                        ],
                        Headers = [
                            #"X-MyFoundry-User-Api-Key" = ApiKeyValue,
                            Accept = "application/json"
                        ]
                    ]
                )
            )
        in
            Source,

    FirstPage = GetPage(1),

    TotalPagesRaw = try FirstPage[metadata][totalPages] otherwise 1,

    TotalPages =
        if TotalPagesRaw = null then
            1
        else
            Number.From(TotalPagesRaw),

    PageNumbers = List.Numbers(1, TotalPages),

    Pages = List.Transform(PageNumbers, each GetPage(_)),

    DataLists = List.Transform(Pages, each try _[data] otherwise {}),

    CombinedData = List.Combine(DataLists),

    RawTable =
        if List.IsEmpty(CombinedData) then
            #table(
                {
                    "id",
                    "geom",
                    "name",
                    "itl1Id",
                    "itl2Id",
                    "localAuthorityId",
                    "date",
                    "ageBand",
                    "incomeBand",
                    "overdraft"
                },
                {}
            )
        else
            Table.FromRecords(CombinedData),

    AddedLongitude = Table.AddColumn(
        RawTable,
        "Longitude",
        each try [geom]{0} otherwise null,
        type number
    ),

    AddedLatitude = Table.AddColumn(
        AddedLongitude,
        "Latitude",
        each try [geom]{1} otherwise null,
        type number
    ),

    RenamedColumns = Table.RenameColumns(
        AddedLatitude,
        {
            {"id", "ID"},
            {"geom", "Geometry"},
            {"name", "Area Name"},
            {"itl1Id", "ITL1 ID"},
            {"itl2Id", "ITL2 ID"},
            {"localAuthorityId", "Local Authority ID"},
            {"date", "Date"},
            {"ageBand", "Age Band"},
            {"incomeBand", "Income Band"},
            {"overdraft", "Overdraft"}
        },
        MissingField.Ignore
    ),

    TypeChanges = {
        {"ID", type text},
        {"Area Name", type text},
        {"ITL1 ID", type text},
        {"ITL2 ID", type text},
        {"Local Authority ID", type text},
        {"Date", type date},
        {"Age Band", type text},
        {"Income Band", type text},
        {"Overdraft", type number},
        {"Longitude", type number},
        {"Latitude", type number}
    },

    ExistingTypeChanges =
        List.Select(
            TypeChanges,
            each List.Contains(Table.ColumnNames(RenamedColumns), _{0})
        ),

    ChangedTypes = Table.TransformColumnTypes(
        RenamedColumns,
        ExistingTypeChanges
    ),

    FilteredCoordinates =
        if List.Contains(Table.ColumnNames(ChangedTypes), "Longitude")
            and List.Contains(Table.ColumnNames(ChangedTypes), "Latitude") then
            Table.SelectRows(
                ChangedTypes,
                each [Longitude] <> null and [Latitude] <> null
            )
        else
            ChangedTypes

in
    FilteredCoordinates

```

### Step 14.4: Rename the Query

Rename the query to:

```text
Overdrawn Accounts

```

Then click **Close & Apply** to load the data into Power BI.

### Step 14.5: Check the Data Transformations

After loading the query, check that your table contains some or all of the following transformed columns. Some columns may be absent depending on the endpoint and filters used.

| Column | Expected Data Type | Purpose |
| --- | --- | --- |
| `ID` | Text | Unique record or area identifier. |
| `Area Name` | Text | Name of the geographic area. |
| `ITL1 ID` | Text | ITL1 geography identifier if returned. |
| `ITL2 ID` | Text | ITL2 geography identifier if returned. |
| `Local Authority ID` | Text | Local authority identifier if returned. |
| `Date` | Date | Date of the observation. |
| `Age Band` | Text | Age band filter value. |
| `Income Band` | Text | Income band filter value. |
| `Overdraft` | Decimal Number | Main metric for the overdrawn accounts endpoint. |
| `Longitude` | Decimal Number | Longitude extracted from `geom`. |
| `Latitude` | Decimal Number | Latitude extracted from `geom`. |

### Step 14.6: Set Data Categories

| Column | Data Category |
| --- | --- |
| `Latitude` | Latitude |
| `Longitude` | Longitude |
| `Area Name` | Place |

### Step 14.7: Create DAX Measures

#### Average Overdraft

```dax
Average Overdraft =
AVERAGE('Overdrawn Accounts'[Overdraft])

```

#### Maximum Overdraft

```dax
Maximum Overdraft =
MAX('Overdrawn Accounts'[Overdraft])

```

#### Minimum Overdraft

```dax
Minimum Overdraft =
MIN('Overdrawn Accounts'[Overdraft])

```

#### Number of Areas

```dax
Number of Areas =
DISTINCTCOUNT('Overdrawn Accounts'[ID])

```

#### Latest Date

```dax
Latest Date =
MAX('Overdrawn Accounts'[Date])

```

#### Average Overdraft on Latest Date

```dax
Average Overdraft Latest Date =
VAR LatestAvailableDate =
    MAX('Overdrawn Accounts'[Date])
RETURN
    CALCULATE(
        [Average Overdraft],
        'Overdrawn Accounts'[Date] = LatestAvailableDate
    )

```

### Step 14.8: Create a Date Table

```dax
Date Table =
CALENDAR(
    MIN('Overdrawn Accounts'[Date]),
    MAX('Overdrawn Accounts'[Date])
)

```

Then add these calculated columns:

```dax
Year =
YEAR('Date Table'[Date])

Month Number =
MONTH('Date Table'[Date])

Month Name =
FORMAT('Date Table'[Date], "MMMM")

Year Month =
FORMAT('Date Table'[Date], "YYYY-MM")

```

Create a relationship between:

```text
'Date Table'[Date] and 'Overdrawn Accounts'[Date]

```

### Step 14.9: Recommended Report Page Layout

Create a report page called:

```text
Economic Wellbeing Overview

```

| Report Area | Visual Type | Purpose |
| --- | --- | --- |
| Top row | Cards | Show headline KPIs. |
| Left side | Slicers | Allow filtering by date, age band, income band, and area. |
| Centre | Azure Maps or Map | Show geographic variation using latitude and longitude. |
| Right side | Clustered Bar Chart | Compare overdraft values by area. |
| Bottom | Line Chart | Show trend over time. |
| Bottom right | Matrix | Compare values by age band and income band. |

### Step 14.10: Add KPI Card Visuals

| Card | Visual Type | Field |
| --- | --- | --- |
| Average Overdraft | Card | `Average Overdraft` |
| Latest Date | Card | `Latest Date` |
| Number of Areas | Card | `Number of Areas` |

### Step 14.11: Add Slicers

| Slicer | Field | Recommended Style |
| --- | --- | --- |
| Date | `Date Table[Date]` | Between |
| Age Band | `Overdrawn Accounts[Age Band]` | Dropdown |
| Income Band | `Overdrawn Accounts[Income Band]` | Dropdown |
| Area Name | `Overdrawn Accounts[Area Name]` | Dropdown with search enabled |

### Step 14.12: Add an Azure Maps Visual

| Azure Maps Field | Power BI Field |
| --- | --- |
| Latitude | `Overdrawn Accounts[Latitude]` |
| Longitude | `Overdrawn Accounts[Longitude]` |
| Size | `Average Overdraft` |
| Color | `Average Overdraft` |
| Tooltips | `Area Name`, `Average Overdraft`, `Age Band`, `Income Band` |

### Step 14.13: Add a Clustered Bar Chart by Area

| Visual Field | Power BI Field |
| --- | --- |
| Y-axis | `Area Name` |
| X-axis | `Average Overdraft` |
| Tooltips | `Maximum Overdraft`, `Minimum Overdraft`, `Number of Areas` |

### Step 14.14: Add a Line Chart for Time Trends

| Visual Field | Power BI Field |
| --- | --- |
| X-axis | `Date Table[Date]` or `Date Table[Year Month]` |
| Y-axis | `Average Overdraft` |
| Legend | `Age Band` or `Income Band` |
| Tooltips | `Average Overdraft`, `Latest Date` |

### Step 14.15: Add a Matrix for Demographic Analysis

| Matrix Field | Power BI Field |
| --- | --- |
| Rows | `Age Band` |
| Columns | `Income Band` |
| Values | `Average Overdraft` |

### Step 14.16: Add a Detail Table

| Table Column |
| --- |
| `Area Name` |
| `Date` |
| `Age Band` |
| `Income Band` |
| `Overdraft` |
| `Latitude` |
| `Longitude` |

### Step 14.17: Recommended Final Visual Combination

> * **Card visuals** for headline KPIs.
> * **Slicers** for date, area, age band, and income band.
> * **Azure Maps** for geographic analysis.
> * **Clustered bar chart** for comparing areas.
> * **Line chart** for trends over time.
> * **Matrix** for age band and income band comparison.
> * **Detail table** for record-level inspection.
> 
> 

---

## 15. Publish and Schedule Refresh

1. Click **Publish** in Power BI Desktop.
2. Choose your Power BI workspace.
3. Go to Power BI Service.
4. Open the semantic model settings.
5. Go to **Data source credentials**.
6. Configure credentials for the web data source.
7. Set up **Scheduled refresh**.

> **Important:** If your API key is rotated, revoked, or expires, Power BI refresh will fail until the stored API key is updated.

---

## 16. Error Handling

Use `try...otherwise` in Power Query to prevent a failed API call from immediately breaking your query during development.

```powerquery
let
    BaseUrl = "https://economic-wellbeing-explorer.services.smartdatafoundry.com",

    ApiKey = "YOUR_API_KEY",

    Response =
        try
            Json.Document(
                Web.Contents(
                    BaseUrl,
                    [
                        RelativePath = "overdrawn-accounts",
                        Headers = [
                            #"X-MyFoundry-User-Api-Key" = ApiKey,
                            Accept = "application/json"
                        ]
                    ]
                )
            )
        otherwise
            null
in
    Response

```

---

## 17. Summary

> 1. Use the production base URL: `https://economic-wellbeing-explorer.services.smartdatafoundry.com`.
> 2. Pass your API key using the `X-MyFoundry-User-Api-Key` header.
> 3. Use endpoints such as `/overdrawn-accounts`, `/emergency-resilience`, and `/living-beyond-means`.
> 4. Use filters such as `geographicLevel`, `areas`, `dateRange`, `ageBand`, `incomeBand`, and `boundingBox`.
> 5. Use pagination with `page` and `size`.
> 6. Convert the JSON `data` array into a Power BI table.
> 7. Extract coordinates from `geom` for map visuals.
> 8. Use the fixed type transformation logic to avoid missing-column errors.
> 9. Create DAX measures and build cards, slicers, maps, charts, matrices, and tables.
> 
> 

---

*Power BI API Integration Guide | MyFoundry Production Data API*
