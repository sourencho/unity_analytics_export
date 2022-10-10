# unity_analytics_export
Python program used to pull Unity Analytics raw data export into a local directory.

Usage:

    python unity_analytics_export.py <path_to_config_file> <start_date> <end_date> 

- The start date (inclusive) of the export. The date is expressed in YYYY-MM-DD format (ISO–8601).

- The end data (exclusive) of the export. The date is expressed in YYYY-MM-DD format (ISO 8601). This is the date at which to close the query. When searching for the current day, use the following day’s date.

Example output:

```
2022-10-10 14:05:55.685276
*** STARTING COLLECTION 2022-09-24 - 2022-09-25 ***
collector: starting collection for job: custom
started jobId: 2dc2318c-8060-4855-be59-71875e8f5702
done! all results for job custom saved to: /Users/sourenpapazian/Documents/code/unity_analytics_export/backup_storage/2022-09-24_2022-09-25
*** COMPLETE ***
```

This program does the following:

1. Requests to export `custom` raw data from Unity Analytics using the HTTP API.
2. Downloads the exported data into several json files in the directory specified. A new direcotry will be created in the format `<collection_path>/start-date_end-date`.

The configuration file must be a valid `json` file containing these parameters:

    {
      "collection_path": "<long term backup path>",
      "unity_project_id":  "<unity project id>",
      "unity_export_api_key": "<unity api key>"
    }

The program has been tested on both Python 2.7.5. and 3.5.2.

Python library dependencies and versions used during development:

1. requests 2.10.0
