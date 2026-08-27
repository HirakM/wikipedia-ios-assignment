# Wikipedia iOS — Places deep link

Fork of [wikipedia-ios](https://github.com/wikimedia/wikipedia-ios) with support for opening the Places tab at coordinates from another app.

Related app: https://github.com/HirakM/places-ios-assignment

## URL format

```
wikipedia://places?lat=<latitude>&long=<longitude>&name=<optional>
```

Examples:

- `wikipedia://places?lat=52.3547498&long=4.8339215&name=Amsterdam`
- `wikipedia://places?latitude=40.4380638&longitude=-3.7495758`

`lat`/`latitude` and `long`/`longitude`/`lon` are accepted.

## What changed

- `NSUserActivity+WMFExtensions` — reads lat/long/name from the Places URL
- `WMFAppViewController` — selects the Places tab and passes coordinates through
- `PlacesViewController` — centers the map and does not jump back to the user location
- Unit tests in `NSUserActivity+WMFExtensionsTest.m`
- `docs/url_schemes.md` updated

On launch the app opens on the Places tab.

## Build

```sh
./scripts/setup
open Wikipedia.xcodeproj
```

Use the Wikipedia scheme (Xcode 16+). Install this build on the same simulator as the Places app before testing deep links.
