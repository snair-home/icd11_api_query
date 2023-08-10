## Code to query ICD-11 API to get the ICD-11 Stem code and title along with post-coordination context of the code.
Example of icd-11 stem code with post coordination extension code separated by "&": KB24&XN0KC

## The code defines three functions that retrieve data from the ICD-11 API:

1. `get_by_codeinfo(codestring, context)`: This function takes a code string and a context as input, and retrieves additional data about the code from the ICD-11 API using the code string. The function returns a JSON object containing the original code string, the context, and any additional data that was retrieved (such as stemId, laterality, hasManifestation, etc.).

2. `get_by_stemid(stemId, context)`: This function takes a stemId and a context as input, and retrieves the code and title associated with the stemId from the ICD-11 API. The function returns a JSON object containing the code, title, and context.

3. `get_icd11_description(response_json, context)`: This function takes a JSON object and a context as input, and retrieves additional data about the code from the JSON object. The function checks if the JSON object contains keys for 'stemId', 'laterality', 'hasManifestation', 'hasCausingCondition', 'associatedWith', or 'infectiousAgent', and if so, it calls the `get_by_codeinfo` and `get_by_stemid` functions to retrieve additional data. The function returns a JSON object containing the original data from the JSON object, as well as any additional data that was retrieved.

4. the final ouptut is a pandas dataframe with stemId and postcoordination context in separate rows.

Note that the code uses the `requests` library to make HTTP requests to the ICD-11 API, and the `json` library to parse JSON data. The code also uses the `headers` variable to specify the headers to be sent with the HTTP requests.
