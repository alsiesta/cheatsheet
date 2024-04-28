## Search Index Comparison (PFox vs. CWOD)

| Field | Type (PFox) | Type (CWOD) | Semantic (PFox) | Semantic (CWOD) | Vector Search - Algorithms (PFox) | Vector Search - Algorithms (CWOD) | Vector Search - Profiles (PFox) | Vector Search - Profiles (CWOD) | Vector Search - Vectorizers (Both) |
|---|---|---|---|---|---|---|---|---|---|
| id | Edm.String | Edm.String | - | - | - | - | - | - | - |
| content | Edm.String | Edm.String | content | content | - | - | - | - | - |
| embedding | Collection(Edm.Single) | Collection(Edm.Single) | - | - | hnsw | hnsw | embedding_config | myHnswProfile | - |
| category | Edm.String | Edm.String | - | - | - | - | - | - | - |
| sourcepage | Edm.String | Edm.String | - | - | - | - | - | - | - |
| sourcefile | Edm.String | Edm.String | - | - | - | - | - | - | - |
| storageUrl | Edm.String | Edm.String | - | - | - | - | - | - | - |
| oids | Collection(Edm.String) | Collection(Edm.String) | - | - | - | - | - | - | - |
| groups | Collection(Edm.String) | Edm.String | - | - | - | - | - | - | - |

**Notes:**

* PFox uses a single semantic configuration with "content" as the prioritized field. CWOD doesn't have a specified semantic configuration in this example.
* Both PFox and CWOD use the Hierarchical Navigable Small World (HNSW) algorithm for vector search.
* Neither PFox nor CWOD define any vectorizers in this example.

**Additional Information:**

* The `type` column shows the data type for each field in both PFox and CWOD.
* The `semantic` column indicates the field used for semantic ranking in PFox and is left blank for CWOD as it doesn't have one specified.
* The `vectorSearch - algorithms` column shows the type of vector search algorithm used (HNSW in this case).
* The `vectorSearch - profiles` column shows the names of the vector search profiles defined.
* The `vectorSearch - vectorizers` column is blank because neither example defines any vectorizers.