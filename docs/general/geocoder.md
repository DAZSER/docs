---
permissions: Administrator
---

# Geocoder

The geocoder will Geocode all entities able to be geocoded. We are currently using geocodio to geocode our entities.
These entities include `"gen_customers", "gen_franchises", "x_prospects", "tm_prospects"`. If the entity fails to be
geocoded, I mark the `bad_address` field with a `1`. If the value of `bad_address` was already a `2` (a successful
sanatization), and the Geocode STILL fails, I mark `bad_address` with a `3`. `3` means `Manual Intervention Needed`.

## Sanatize Address

Sanatize Addresses is a sub component of the Geocoder, which is found in `sanatize-addresses.ts`. It will take all the
addresses for `"gen_customers_business", "gen_franchises", // "x_prospects", "tm_prospects",`, and clean them by using
the USPS's API. If the value of the address is sanatized, `bad_address` is updated with a `2`.

| `bad_address` | Meaning                                       |
| ------------- | --------------------------------------------- |
| `0`           | Valid, Found, and Sanatized address & geocode |
| `1`           | Bad Original Address                          |
| `2`           | Updated USPS Address, needs Geocode           |
| `3`           | Unable to Verify address                      |

| Permissions       | Last Updated                                     |
| ----------------- | ------------------------------------------------ |
| {{ permissions }} | {{ git.date.strftime("%b %d, %Y %I:%M:%S %p") }} |
