# Cost of Living Adjustments
> This page was last updated: {{ git_revision_date_localized }}

To upload a Cost of Living Adjustment file, put a new CSV file with the column titles of
`id,lastColaAmount,lastColaDate,newAmount` to the S3 Bucket `s3://dazser-files/cola/region/*.csv`. This will kick off
`backend/cola.ts#default()` run which will process the CSV file and upload the results to specified
region.

|  | Level |
| --- | --- |
| Permissions | Administrator |
