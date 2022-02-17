---
permissions: Administrator
---
# Cost of Living Adjustments
To upload a Cost of Living Adjustment file, upload a new CSV file with the column titles of
`id,lastColaAmount,lastColaDate,newAmount` to the S3 Bucket `s3://dazser-files/cola/{{regionName}}/*.csv`. This will
kick off [`backend/cola.ts`](https://github.com/DAZSER/backend/blob/master/src/cola.ts) which will process the
CSV file and upload the results to specified region.

| regionName | Region     |
| ---------- | ---------- |
| baltimore  | Baltimore  |
| birmingham | Birmingham |
| orlando    | Orlando    |
| tampa      | Tampa      |


Example:
```
s3://dazser-files/cola/tampa/colafor2022.csv
---
id,newAmount,lastColaDate,lastColaAmount
4517,1168,10/1/2021,1
7497,1,10/1/2021,1
```
Permissions | Last Updated
--- | ---
{{ permissions }} | {{ git.date.strftime("%b %d, %Y %I:%M:%S %p") }}
