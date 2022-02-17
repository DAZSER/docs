---
permissions: Administrator
---

# Uploading new prospects into the web app

In order to add new prospects into the web app, a CSV file must be uploaded to
`s3://dazser-files/prospects/{{region}}/{{listSource}}/*.csv` where `region` is the name of the region, and `listSource`
is the source of the list.

| listSource  | List Source         | Definition for the CSV file                                                 |
| ----------- | ------------------- | --------------------------------------------------------------------------- |
| infousa     | InfoUSA             | https://github.com/DAZSER/backend/blob/master/src/upload-x-prospects.ts#L37 |
| jkcorporate | Jani-King Corporate | https://github.com/DAZSER/backend/blob/master/src/upload-x-prospects.ts#L54 |
| customers   | Our Customers table | https://github.com/DAZSER/backend/blob/master/src/upload-x-prospects.ts#L69 |

| regionName | Region     |
| ---------- | ---------- |
| baltimore  | Baltimore  |
| birmingham | Birmingham |
| orlando    | Orlando    |
| tampa      | Tampa      |

This will upload the prospects into the `x_prospects` table. The next step is to run the geocoder. This should be
running every 15 minutes, but may not be for `x_prospects`.

## Deduplicate TM Prospects
Finally, run `deduplicate-x-prospects.ts`. This
is a Lambda function that must be invoked. (This is not setup to be automatic yet,
[tracked here](https://github.com/DAZSER/backend/issues/59)). This function will clean up all the NAICS codes, remove
any obvious duplicates (Same InfoUSA number, same exact geocode), deal with bad zip codes, etc...

| Permissions       | Last Updated                                     |
| ----------------- | ------------------------------------------------ |
| {{ permissions }} | {{ git.date.strftime("%b %d, %Y %I:%M:%S %p") }} |
