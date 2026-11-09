# ng.nways:client (Kotlin)

The N-Ways Maps Platform API client for the JVM (17+) and Android: one method per API operation (geocoding, postcodes, places,
routes, the route matrix, fares, static maps, fleet tracking…), your key in the `X-NWays-Api-Key` header, and errors
with the HTTP status, the `reason` and `Retry-After`. Generated from the N-Ways OpenAPI files.

Docs: https://nways.ng/developers/client-libraries · API reference: https://nways.ng/developers/reference

## Install

```kotlin
dependencies { implementation("ng.nways:client:1.1.0") }
```

## Example

```kotlin
import ng.nways.client.ApiError
import ng.nways.client.NWaysClient

val nways = NWaysClient(apiKey = System.getenv("NWAYS_API_KEY"))
// Calls block: run them on Dispatchers.IO in an app.
try {
    val answer = nways.geocode(q = "Allen Avenue, Ikeja", limit = 3)
    println(answer.results.firstOrNull()?.name)
} catch (e: ApiError) {
    println("${e.status} ${e.reason}")
}
```

Keep server keys (restricted to your servers' IP addresses) out of web pages and apps.

## Licence

The client's code is licensed under the [Apache License, Version 2.0](LICENSE) (`Apache-2.0`), Copyright 2026
N-WAYS LIMITED; see [NOTICE](NOTICE).

The licence covers the code, not the data the API returns. N-Ways maps and data are built on OpenStreetMap,
© OpenStreetMap contributors, available under the [Open Database License (ODbL)](https://www.openstreetmap.org/copyright);
credit "N-Ways · © OpenStreetMap contributors" wherever you show them. Using the API needs an N-Ways API key and is
governed by the [N-Ways Maps Platform terms](https://nways.ng/developers/terms).
