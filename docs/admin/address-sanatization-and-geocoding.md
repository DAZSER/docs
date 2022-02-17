# Address Sanatization and Geocoding

1. The entity gets added and we sanatize the Address according to the USPS, `bad_address` is set to `0`.
1. Every 15 minutes, I attempt to Geocode any address that has a `bad_address` of `0` or `2`.


`bad_address` | Meaning
--- | ---
`0` | Valid, Found, and Sanatized address & geocode
`1` | Bad Original Address
`2` | Updated USPS Address, needs Geocode
`3` | Unable to Verify address
