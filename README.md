# aw-watcher-web

[![Chrome Web Store](https://img.shields.io/chrome-web-store/v/nglaklhklhcoonedhgnpgddginnjdadi.svg)][chrome]
[![Mozilla Add-on](https://img.shields.io/amo/v/aw-watcher-web.svg)][firefox]

A cross-browser WebExtension that serves as a web browser watcher for [ActivityWatch][activitywatch].


## Usage

Install for your browser:

 - [Chrome][chrome]
 - ~~Firefox~~
   - Due to Mozilla incompetency, the addon is no longer listed in the Mozilla Addons store (see [discussion #818][818]).
   - ~~You can install the latest Mozilla-signed version [here][last-xpi].~~ (we are apparently not allowed to self-distribute this, see discussion linked above)
   - You can also build from source, see [this comment][build-source-cmt] and instructions below.

[activitywatch]: https://github.com/ActivityWatch/activitywatch
[firefox]: https://addons.mozilla.org/en-US/firefox/addon/aw-watcher-web/
[chrome]: https://chrome.google.com/webstore/detail/nglaklhklhcoonedhgnpgddginnjdadi/
[build-source-cmt]: https://github.com/ActivityWatch/aw-watcher-web/issues/94#issuecomment-1315773537
[last-xpi]: https://github.com/ActivityWatch/aw-watcher-web/releases/download/v0.4.3/aw-watcher-web-v0.4.3.xpi
[818]: https://github.com/orgs/ActivityWatch/discussions/818#discussioncomment-4017528

### Firefox Enterprise Policy

Due to the issue mentioned above, a privacy notice has to be displayed to follow the Mozilla add-on policy. This can be pre-accepted by setting the following Firefox Enterprise Policy:
```json
{
  "policies": {
    "3rdparty": {
      "Extensions": {
        "{ef87d84c-2127-493f-b952-5b4e744245bc}": {
          "consentOfflineDataCollection": true
        }
      }
    }
  }
}
```

## Building

First, clone the repo with:

```sh
git pull --recurse-submodules https://github.com/ActivityWatch/aw-watcher-web.git
# or, normal `git pull` and then:
git submodule update --init
```

Then build with:

```
make build
```

The resulting `aw-watcher-web.zip` can then be loaded into your browser in development mode. (for Firefox, loading unsigned extensions is only possible in Firefox Nightly and Developer Edition).

For further build instructions, refer to the `Makefile`.
