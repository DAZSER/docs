---
permissions: Administrator
---
# The Funnel

## Moving Propsects from Sales Rep funnel to TM funnel
Prospects are automatically moved to the TM funnel if they haven't been called in the past 18 months. This is done via
`move-sr-prospects-to-tm-prospects.ts` and it runs every 7 days.

Permissions | Last Updated
--- | ---
{{ permissions }} | {{ git.date.strftime("%b %d, %Y %I:%M:%S %p") }}
