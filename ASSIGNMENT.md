# Wikipedia iOS — Places deep link

Fork of [wikipedia-ios](https://github.com/wikimedia/wikipedia-ios) that opens the Places tab at coordinates provided by another app.

Related app: https://github.com/HirakM/places-ios-assignment

## Behavior

- App launch selects the **Places** tab
- `wikipedia://places?lat=&long=&name=` centers the map on those coordinates
- Device location is not used to override a deep-linked position

## URL format

```
wikipedia://places?lat=<latitude>&long=<longitude>&name=<optional>
```

Also accepts `latitude` / `longitude` / `lon`.

Examples:

- `wikipedia://places?lat=52.3547498&long=4.8339215&name=Amsterdam`
- `wikipedia://places?latitude=40.4380638&longitude=-3.7495758`

## Code touchpoints

| Area | Role |
|------|------|
| `NSUserActivity+WMFExtensions` | Parses Places URL query into activity userInfo |
| `WMFAppViewController` | Routes to Places and calls `showLocation` |
| `PlacesViewController` | Centers map; skips user-location recenter when deep-linked |
| `NSUserActivity+WMFExtensionsTest` | Covers coordinate query parsing |
| `docs/url_schemes.md` | Documents the URL |

## Build

```sh
./scripts/setup
open Wikipedia.xcodeproj
```

Run the Wikipedia scheme, then exercise deep links from the Places app on the same simulator.
