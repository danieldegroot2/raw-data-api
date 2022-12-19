<!--
This Markdown has been generated by essentials-openapi
https://github.com/Neoteroi/essentials-openapi

Most likely, it is not desirable to edit this file by hand!
-->

# Export tool API <span class="api-version">1</span>


## Servers

<table>
    <thead>
        <tr>
            <th>Description</th>
            <th>URL</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>/latest</td>
            <td>
                <a href="/latest" target="_blank" rel="noopener noreferrer">/latest</a>
            </td>
        </tr>
    </tbody>
</table>

## <span class="api-tag"></span>

<hr class="operation-separator" />

### <span class="http-get">GET</span> /status/
Check Database Last Updated

??? note "Description"
    Gives status about how recent the osm data is , it will give the last time
    that database was updated completely


<p class="response-title">
    <strong>Response <span class="response-code code-200">200</span>&nbsp;<span class="status-phrase">OK</span></strong>
</p>

=== "application/json"
    
    
    ```json
    {
        "lastUpdated": "2022-06-27 19:59:24+05:45"
    }
    ```
    <span class="small-note">⚠️</span>&nbsp;<em class="small-note warning">This example has been generated automatically from the schema and it is not accurate. Refer to the schema for more information.</em>

    

    ??? hint "Schema of the response body"
        ```json
        {
            "title": "StatusResponse",
            "required": [
                "lastUpdated"
            ],
            "type": "object",
            "properties": {
                "lastUpdated": {
                    "title": "Lastupdated",
                    "type": "string"
                }
            },
            "additionalProperties": false,
            "example": {
                "lastUpdated": "2022-06-27 19:59:24+05:45"
            }
        }
        ```



<hr class="operation-separator" />

### <span class="http-post">POST</span> /snapshot/
Get Osm Current Snapshot As File

??? note "Description"
    Generates the current raw OpenStreetMap data available on database based on
    the input geometry, query and spatial features.

    Steps to Run Snapshot :

    1.  Post the your request here and your request will be on queue, endpoint
    will return as following :
        {
            &#34;task_id&#34;: &#34;your task_id&#34;,
            &#34;track_link&#34;: &#34;/tasks/task_id/&#34;
        }
    2. Now navigate to /tasks/ with your task id to track progress and result

<p class="request-body-title"><strong>Request body</strong></p>



=== "application/json"
    
    
    ```json
    {
        "geometry": {
            "type": "Polygon",
            "coordinates": [
                [
                    [
                        83.96919250488281,
                        28.194446860487773
                    ],
                    [
                        83.99751663208006,
                        28.194446860487773
                    ],
                    [
                        83.99751663208006,
                        28.214869548073377
                    ],
                    [
                        83.96919250488281,
                        28.214869548073377
                    ],
                    [
                        83.96919250488281,
                        28.194446860487773
                    ]
                ]
            ]
        }
    }
    ```
    

    
    ```json
    {
        "outputType": "shp",
        "fileName": "Pokhara_all_features",
        "geometry": {
            "type": "Polygon",
            "coordinates": [
                [
                    [
                        83.96919250488281,
                        28.194446860487773
                    ],
                    [
                        83.99751663208006,
                        28.194446860487773
                    ],
                    [
                        83.99751663208006,
                        28.214869548073377
                    ],
                    [
                        83.96919250488281,
                        28.214869548073377
                    ],
                    [
                        83.96919250488281,
                        28.194446860487773
                    ]
                ]
            ]
        }
    }
    ```
    

    
    ```json
    {
        "outputType": "geojson",
        "fileName": "Pokhara_buildings",
        "geometry": {
            "type": "Polygon",
            "coordinates": [
                [
                    [
                        83.96919250488281,
                        28.194446860487773
                    ],
                    [
                        83.99751663208006,
                        28.194446860487773
                    ],
                    [
                        83.99751663208006,
                        28.214869548073377
                    ],
                    [
                        83.96919250488281,
                        28.214869548073377
                    ],
                    [
                        83.96919250488281,
                        28.194446860487773
                    ]
                ]
            ]
        },
        "filters": {
            "tags": {
                "all_geometry": {
                    "building": []
                }
            },
            "attributes": {
                "all_geometry": [
                    "name"
                ]
            }
        },
        "geometryType": [
            "point",
            "polygon"
        ]
    }
    ```
    

    
    ```json
    {
        "geometry": {
            "type": "Polygon",
            "coordinates": [
                [
                    [
                        83.585701,
                        28.046607
                    ],
                    [
                        83.585701,
                        28.382561
                    ],
                    [
                        84.391823,
                        28.382561
                    ],
                    [
                        84.391823,
                        28.046607
                    ],
                    [
                        83.585701,
                        28.046607
                    ]
                ]
            ]
        },
        "fileName": "my export",
        "outputType": "geojson",
        "geometryType": [
            "point",
            "polygon"
        ],
        "filters": {
            "tags": {
                "all_geometry": {
                    "building": [],
                    "amenity": [
                        "cafe",
                        "restaurant",
                        "pub"
                    ]
                }
            },
            "attributes": {
                "all_geometry": [
                    "name",
                    "addr"
                ]
            }
        },
        "joinFilterType": "OR"
    }
    ```
    

    
    ```json
    {
        "fileName": "Example export with all features",
        "geometry": {
            "type": "Polygon",
            "coordinates": [
                [
                    [
                        83.585701,
                        28.046607
                    ],
                    [
                        83.585701,
                        28.382561
                    ],
                    [
                        84.391823,
                        28.382561
                    ],
                    [
                        84.391823,
                        28.046607
                    ],
                    [
                        83.585701,
                        28.046607
                    ]
                ]
            ]
        },
        "outputType": "geojson",
        "geometryType": [
            "point",
            "line",
            "polygon"
        ],
        "filters": {
            "tags": {
                "point": {
                    "amenity": [
                        "bank",
                        "ferry_terminal",
                        "bus_station",
                        "fuel",
                        "kindergarten",
                        "school",
                        "college",
                        "university",
                        "place_of_worship",
                        "marketplace",
                        "clinic",
                        "hospital",
                        "police",
                        "fire_station"
                    ],
                    "building": [
                        "bank",
                        "aerodrome",
                        "ferry_terminal",
                        "train_station",
                        "bus_station",
                        "pumping_station",
                        "power_substation",
                        "kindergarten",
                        "school",
                        "college",
                        "university",
                        "mosque ",
                        " church ",
                        " temple",
                        "supermarket",
                        "marketplace",
                        "clinic",
                        "hospital",
                        "police",
                        "fire_station",
                        "stadium ",
                        " sports_centre",
                        "governor_office ",
                        " townhall ",
                        " subdistrict_office ",
                        " village_office ",
                        " community_group_office",
                        "government_office"
                    ],
                    "man_made": [
                        "tower",
                        "water_tower",
                        "pumping_station"
                    ],
                    "tower:type": [
                        "communication"
                    ],
                    "aeroway": [
                        "aerodrome"
                    ],
                    "railway": [
                        "station"
                    ],
                    "emergency": [
                        "fire_hydrant"
                    ],
                    "landuse": [
                        "reservoir",
                        "recreation_gound"
                    ],
                    "waterway": [
                        "floodgate"
                    ],
                    "natural": [
                        "spring"
                    ],
                    "power": [
                        "tower",
                        "substation"
                    ],
                    "shop": [
                        "supermarket"
                    ],
                    "leisure": [
                        "stadium ",
                        " sports_centre ",
                        " pitch ",
                        " swimming_pool",
                        "park"
                    ],
                    "office": [
                        "government"
                    ]
                },
                "line": {
                    "highway": [
                        "motorway ",
                        " trunk ",
                        " primary ",
                        " secondary ",
                        " tertiary ",
                        " service ",
                        " residential ",
                        " pedestrian ",
                        " path ",
                        " living_street ",
                        " track"
                    ],
                    "railway": [
                        "rail"
                    ],
                    "man_made": [
                        "embankment"
                    ],
                    "waterway": []
                },
                "polygon": {
                    "amenity": [
                        "bank",
                        "ferry_terminal",
                        "bus_station",
                        "fuel",
                        "kindergarten",
                        "school",
                        "college",
                        "university",
                        "place_of_worship",
                        "marketplace",
                        "clinic",
                        "hospital",
                        "police",
                        "fire_station"
                    ],
                    "building": [
                        "bank",
                        "aerodrome",
                        "ferry_terminal",
                        "train_station",
                        "bus_station",
                        "pumping_station",
                        "power_substation",
                        "power_plant",
                        "kindergarten",
                        "school",
                        "college",
                        "university",
                        "mosque ",
                        " church ",
                        " temple",
                        "supermarket",
                        "marketplace",
                        "clinic",
                        "hospital",
                        "police",
                        "fire_station",
                        "stadium ",
                        " sports_centre",
                        "governor_office ",
                        " townhall ",
                        " subdistrict_office ",
                        " village_office ",
                        " community_group_office",
                        "government_office"
                    ],
                    "man_made": [
                        "tower",
                        "water_tower",
                        "pumping_station"
                    ],
                    "tower:type": [
                        "communication"
                    ],
                    "aeroway": [
                        "aerodrome"
                    ],
                    "railway": [
                        "station"
                    ],
                    "landuse": [
                        "reservoir",
                        "recreation_gound"
                    ],
                    "waterway": [],
                    "natural": [
                        "spring"
                    ],
                    "power": [
                        "substation",
                        "plant"
                    ],
                    "shop": [
                        "supermarket"
                    ],
                    "leisure": [
                        "stadium ",
                        " sports_centre ",
                        " pitch ",
                        " swimming_pool",
                        "park"
                    ],
                    "office": [
                        "government"
                    ],
                    "type": [
                        "boundary"
                    ],
                    "boundary": [
                        "administrative"
                    ]
                }
            },
            "attributes": {
                "point": [
                    "building",
                    "ground_floor:height",
                    "capacity:persons",
                    "building:structure",
                    "building:condition",
                    "name",
                    "admin_level",
                    "building:material",
                    "office",
                    "building:roof",
                    "backup_generator",
                    "access:roof",
                    "building:levels",
                    "building:floor",
                    "addr:full",
                    "addr:city",
                    "source"
                ],
                "line": [
                    "width",
                    "source",
                    "waterway",
                    "name"
                ],
                "polygon": [
                    "landslide_prone",
                    "name",
                    "admin_level",
                    "type",
                    "is_in:town",
                    "flood_prone",
                    "is_in:province",
                    "is_in:city",
                    "is_in:municipality",
                    "is_in:RW",
                    "is_in:village",
                    "source",
                    "boundary"
                ]
            }
        }
    }
    ```
    

    

    ??? hint "Schema of the request body"
        ```json
        {
            "title": "Params",
            "allOf": [
                {
                    "$ref": "#/components/schemas/RawDataCurrentParams"
                }
            ],
            "default": {}
        }
        ```



<p class="response-title">
    <strong>Response <span class="response-code code-200">200</span>&nbsp;<span class="status-phrase">OK</span></strong>
</p>

=== "application/json"
    
    
    ```json
    {
        "task_id": "aa539af6-83d4-4aa3-879e-abf14fffa03f",
        "track_link": "/tasks/status/aa539af6-83d4-4aa3-879e-abf14fffa03f/"
    }
    ```
    <span class="small-note">⚠️</span>&nbsp;<em class="small-note warning">This example has been generated automatically from the schema and it is not accurate. Refer to the schema for more information.</em>

    

    ??? hint "Schema of the response body"
        ```json
        {
            "title": "SnapshotResponse",
            "required": [
                "taskId",
                "trackLink"
            ],
            "type": "object",
            "properties": {
                "taskId": {
                    "title": "Taskid",
                    "type": "string"
                },
                "trackLink": {
                    "title": "Tracklink",
                    "type": "string"
                }
            },
            "additionalProperties": false,
            "example": {
                "task_id": "aa539af6-83d4-4aa3-879e-abf14fffa03f",
                "track_link": "/tasks/status/aa539af6-83d4-4aa3-879e-abf14fffa03f/"
            }
        }
        ```



<p class="response-title">
    <strong>Response <span class="response-code code-422">422</span>&nbsp;<span class="status-phrase">Unprocessable Entity</span></strong>
</p>

=== "application/json"
    
    
    ```json
    {
        "detail": [
            {
                "loc": [
                    "string"
                ],
                "msg": "string",
                "type": "string"
            }
        ]
    }
    ```
    <span class="small-note">⚠️</span>&nbsp;<em class="small-note warning">This example has been generated automatically from the schema and it is not accurate. Refer to the schema for more information.</em>

    

    ??? hint "Schema of the response body"
        ```json
        {
            "title": "HTTPValidationError",
            "type": "object",
            "properties": {
                "detail": {
                    "title": "Detail",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/ValidationError"
                    }
                }
            }
        }
        ```



<hr class="operation-separator" />

### <span class="http-post">POST</span> /snapshot/plain/
Get Current Snapshot As Plain Geojson

??? note "Description"
    Simple API to get osm features as geojson for small region. This is designed
    only for querying small data for large data follow /snapshot/

    Params ::

        bbox: Optional List = takes xmin, ymin, xmax, ymax uses srid=4326
        select: List = this is select query  you can pass [*] to select all
    attribute
        where: List[WhereCondition] = [{&#39;key&#39;: &#39;building&#39;, &#39;value&#39;:
    [&#39;*&#39;]},{&#39;key&#39;:&#39;amenity&#39;,&#39;value&#39;:[&#39;school&#39;,&#39;college&#39;]}]
        join_by: Optional[JoinFilterType] = or/ and
        look_in: Optional[List[OsmFeatureType]] = [&#34;nodes&#34;,
    &#34;ways_poly&#34;,&#34;ways_line&#34;,&#34;relations&#34;] : tables name

<p class="request-body-title"><strong>Request body</strong></p>



=== "application/json"
    
    
    ```json
    {
        "select": [
            "name"
        ],
        "where": [
            {
                "key": "admin_level",
                "value": [
                    "2"
                ]
            },
            {
                "key": "boundary",
                "value": [
                    "administrative"
                ]
            },
            {
                "key": "name:en",
                "value": [
                    "Nepal"
                ]
            }
        ],
        "joinBy": "AND",
        "lookIn": [
            "relations"
        ]
    }
    ```
    

    
    ```json
    {
        "select": [
            "name"
        ],
        "where": [
            {
                "key": "admin_level",
                "value": [
                    "7"
                ]
            },
            {
                "key": "boundary",
                "value": [
                    "administrative"
                ]
            },
            {
                "key": "name",
                "value": [
                    "Pokhara"
                ]
            }
        ],
        "joinBy": "AND",
        "lookIn": [
            "relations"
        ]
    }
    ```
    

    

    ??? hint "Schema of the request body"
        ```json
        {
            "title": "Params",
            "allOf": [
                {
                    "$ref": "#/components/schemas/SnapshotParamsPlain"
                }
            ],
            "default": {}
        }
        ```



<p class="response-title">
    <strong>Response <span class="response-code code-200">200</span>&nbsp;<span class="status-phrase">OK</span></strong>
</p>

=== "application/json"
    
    

    ??? hint "Schema of the response body"
        ```json
        {
            "title": "Response Get Current Snapshot As Plain Geojson Snapshot Plain  Post",
            "type": "object"
        }
        ```



<p class="response-title">
    <strong>Response <span class="response-code code-422">422</span>&nbsp;<span class="status-phrase">Unprocessable Entity</span></strong>
</p>

=== "application/json"
    
    
    ```json
    {
        "detail": [
            {
                "loc": [
                    "string"
                ],
                "msg": "string",
                "type": "string"
            }
        ]
    }
    ```
    <span class="small-note">⚠️</span>&nbsp;<em class="small-note warning">This example has been generated automatically from the schema and it is not accurate. Refer to the schema for more information.</em>

    

    ??? hint "Schema of the response body"
        ```json
        {
            "title": "HTTPValidationError",
            "type": "object",
            "properties": {
                "detail": {
                    "title": "Detail",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/ValidationError"
                    }
                }
            }
        }
        ```



<hr class="operation-separator" />

### <span class="http-get">GET</span> /tasks/status/<span class="route-param">{task_id}</span>/
Get Task Status

??? note "Description"
    Tracks the request from the task id provided by export tool api for the
    request

    Args:

        task_id ([type]): [Unique id provided on response from /snapshot/]

    Returns:

        id: Id of the task
        status : SUCCESS / PENDING
        result : Result of task

    Successful task will have additional nested json inside


**Input parameters**

<table>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>In</th>
            <th>Type</th>
            <th>Default</th>
            <th>Nullable</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="parameter-name"><code>task_id</code></td>
            <td>path</td>
            <td>None</td>
            <td></td>
            <td>No</td>
            <td></td>
        </tr>
    </tbody>
</table>

<p class="response-title">
    <strong>Response <span class="response-code code-200">200</span>&nbsp;<span class="status-phrase">OK</span></strong>
</p>

=== "application/json"
    
    
    ```json
    {
        "id": "3fded368-456f-4ef4-a1b8-c099a7f77ca4",
        "status": "SUCCESS",
        "result": {
            "download_url": "https://s3.us-east-1.amazonaws.com/exports-stage.hotosm.org/Raw_Export_3fded368-456f-4ef4-a1b8-c099a7f77ca4_GeoJSON.zip",
            "file_name": "Raw_Export_3fded368-456f-4ef4-a1b8-c099a7f77ca4_GeoJSON",
            "response_time": "0:00:12.175976",
            "query_area": "6 Sq Km ",
            "binded_file_size": "7 MB",
            "zip_file_size_bytes": 1331601
        }
    }
    ```
    <span class="small-note">⚠️</span>&nbsp;<em class="small-note warning">This example has been generated automatically from the schema and it is not accurate. Refer to the schema for more information.</em>

    

    ??? hint "Schema of the response body"
        ```json
        {
            "title": "SnapshotTaskResponse",
            "required": [
                "id",
                "status",
                "result"
            ],
            "type": "object",
            "properties": {
                "id": {
                    "title": "Id",
                    "type": "string"
                },
                "status": {
                    "title": "Status",
                    "type": "string"
                },
                "result": {
                    "$ref": "#/components/schemas/SnapshotTaskResult"
                }
            },
            "additionalProperties": false,
            "example": {
                "id": "3fded368-456f-4ef4-a1b8-c099a7f77ca4",
                "status": "SUCCESS",
                "result": {
                    "download_url": "https://s3.us-east-1.amazonaws.com/exports-stage.hotosm.org/Raw_Export_3fded368-456f-4ef4-a1b8-c099a7f77ca4_GeoJSON.zip",
                    "file_name": "Raw_Export_3fded368-456f-4ef4-a1b8-c099a7f77ca4_GeoJSON",
                    "response_time": "0:00:12.175976",
                    "query_area": "6 Sq Km ",
                    "binded_file_size": "7 MB",
                    "zip_file_size_bytes": 1331601
                }
            }
        }
        ```



<p class="response-title">
    <strong>Response <span class="response-code code-422">422</span>&nbsp;<span class="status-phrase">Unprocessable Entity</span></strong>
</p>

=== "application/json"
    
    
    ```json
    {
        "detail": [
            {
                "loc": [
                    "string"
                ],
                "msg": "string",
                "type": "string"
            }
        ]
    }
    ```
    <span class="small-note">⚠️</span>&nbsp;<em class="small-note warning">This example has been generated automatically from the schema and it is not accurate. Refer to the schema for more information.</em>

    

    ??? hint "Schema of the response body"
        ```json
        {
            "title": "HTTPValidationError",
            "type": "object",
            "properties": {
                "detail": {
                    "title": "Detail",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/ValidationError"
                    }
                }
            }
        }
        ```






---
## Schemas


### AttributeFilter

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>allGeometry</code></td>
            <td>Array&lt;<span class="string-type">string</span>&gt;</td>
        </tr>
        <tr>
            <td><code>line</code></td>
            <td>Array&lt;<span class="string-type">string</span>&gt;</td>
        </tr>
        <tr>
            <td><code>point</code></td>
            <td>Array&lt;<span class="string-type">string</span>&gt;</td>
        </tr>
        <tr>
            <td><code>polygon</code></td>
            <td>Array&lt;<span class="string-type">string</span>&gt;</td>
        </tr>
    </tbody>
</table>



### Filters

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>attributes</code></td>
            <td><a href="#attributefilter" class="ref-link">AttributeFilter</a></td>
        </tr>
        <tr>
            <td><code>tags</code></td>
            <td><a href="#tagsfilter" class="ref-link">TagsFilter</a></td>
        </tr>
    </tbody>
</table>



### HTTPValidationError

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>detail</code></td>
            <td>Array&lt;<a href="#validationerror" class="ref-link">ValidationError</a>&gt;</td>
        </tr>
    </tbody>
</table>



### JoinFilterType
<span>Type: </span>



### MultiPolygon

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>coordinates</code></td>
            <td>Array&lt;Array&lt;Array&lt;&gt;&gt;&gt;</td>
        </tr>
        <tr>
            <td><code>type</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
    </tbody>
</table>



### OsmFeatureType
<span>Type: </span>



### Polygon

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>coordinates</code></td>
            <td>Array&lt;Array&lt;&gt;&gt;</td>
        </tr>
        <tr>
            <td><code>type</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
    </tbody>
</table>



### RawDataCurrentParams

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>countryExport</code></td>
            <td><span class="boolean-type">boolean</span></td>
        </tr>
        <tr>
            <td><code>fileName</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>filters</code></td>
            <td></td>
        </tr>
        <tr>
            <td><code>geometry</code></td>
            <td></td>
        </tr>
        <tr>
            <td><code>geometryType</code></td>
            <td>Array&lt;<a href="#supportedgeometryfilters" class="ref-link">SupportedGeometryFilters</a>&gt;</td>
        </tr>
        <tr>
            <td><code>joinFilterType</code></td>
            <td></td>
        </tr>
        <tr>
            <td><code>maxZoom</code></td>
            <td><span class="integer-type">integer</span></td>
        </tr>
        <tr>
            <td><code>minZoom</code></td>
            <td><span class="integer-type">integer</span></td>
        </tr>
        <tr>
            <td><code>outputType</code></td>
            <td></td>
        </tr>
    </tbody>
</table>



### RawDataOutputType
<span>Type: </span>



### SnapshotParamsPlain

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>bbox</code></td>
            <td></td>
        </tr>
        <tr>
            <td><code>geometryType</code></td>
            <td><a href="#supportedgeometryfilters" class="ref-link">SupportedGeometryFilters</a></td>
        </tr>
        <tr>
            <td><code>joinBy</code></td>
            <td></td>
        </tr>
        <tr>
            <td><code>lookIn</code></td>
            <td>Array&lt;<a href="#osmfeaturetype" class="ref-link">OsmFeatureType</a>&gt;</td>
        </tr>
        <tr>
            <td><code>select</code></td>
            <td>Array&lt;<span class="string-type">string</span>&gt;</td>
        </tr>
        <tr>
            <td><code>where</code></td>
            <td>Array&lt;<a href="#wherecondition" class="ref-link">WhereCondition</a>&gt;</td>
        </tr>
    </tbody>
</table>



### SnapshotResponse

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>taskId</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>trackLink</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
    </tbody>
</table>



### SnapshotTaskResponse

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>id</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>result</code></td>
            <td><a href="#snapshottaskresult" class="ref-link">SnapshotTaskResult</a></td>
        </tr>
        <tr>
            <td><code>status</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
    </tbody>
</table>



### SnapshotTaskResult

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>bindedFileSize</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>downloadUrl</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>fileName</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>queryArea</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>responseTime</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>zipFileSizeBytes</code></td>
            <td><span class="integer-type">integer</span></td>
        </tr>
    </tbody>
</table>



### StatusResponse

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>lastUpdated</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
    </tbody>
</table>



### SupportedGeometryFilters
<span>Type: </span>



### TagsFilter

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>allGeometry</code></td>
            <td></td>
        </tr>
        <tr>
            <td><code>line</code></td>
            <td></td>
        </tr>
        <tr>
            <td><code>point</code></td>
            <td></td>
        </tr>
        <tr>
            <td><code>polygon</code></td>
            <td></td>
        </tr>
    </tbody>
</table>



### ValidationError

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>loc</code></td>
            <td>Array&lt;<span class="string-type">string</span>&gt;</td>
        </tr>
        <tr>
            <td><code>msg</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>type</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
    </tbody>
</table>



### WhereCondition

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>key</code></td>
            <td><span class="string-type">string</span></td>
        </tr>
        <tr>
            <td><code>value</code></td>
            <td>Array&lt;<span class="string-type">string</span>&gt;</td>
        </tr>
    </tbody>
</table>

