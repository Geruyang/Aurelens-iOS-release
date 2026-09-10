# Build 18 capture and repository update — 2026-09-10

The second capture round verified the already installed Aurelens 0.6.3 / build 18 on an iPhone 17 Pro Max (physical iOS 27.0) and iPad Pro 13-inch (M5) simulator (26.5). It produced 28 native PNGs and two silent H.264 review recordings (iPhone 128 seconds; iPad 144 seconds). All three navigation/capture runs passed with zero failures. iPad was retaken after a temporary live-source/demo fallback; final captures were inspected.

The original desktop material set is at `截图/build18/第二轮-20260910-2300`. Earlier material files remain unchanged. Full XCTest results and recordings are retained locally under `build/recapture18-20260910-2300`; reusable capture sources are in `tools/capture-build18` in the private source repository. Device identifiers, complete logs and development-signed packages are not included in the public media bundle.

Public final media: https://github.com/Geruyang/Aurelens-iOS-release/tree/main/AppStore-Media/0.6.3-build18/2026-09-10-round2

Both repositories use the new version branch `codex/v0.6.3-build18-materials`. The private source repository is `Geruyang/Aurelens-iOS`; the public artifact repository is `Geruyang/Aurelens-iOS-release`. Their local folders remain `AutoGolden-iOS` and `AutoGolden-iOS-release`. Historical tags, releases, IPA files and historical filenames are preserved.

## Build and website boundary

No application source, bundle identifier or binary was changed by this repository/material update. The original `v0.6.3-build18` tag remains the reproducible source for the existing binary. This update does not claim complete physical-device functional testing or App Store submission.

The current website addresses are:

- https://geruyang.github.io/Aurelens-iOS-release/
- https://geruyang.github.io/Aurelens-iOS-release/privacy.html
- https://geruyang.github.io/Aurelens-iOS-release/support.html

GitHub repository redirects do not cover GitHub Pages project URLs. The archived build 18 binary and its matching source still contain `https://geruyang.github.io/AutoGolden-iOS-release/` policy links. Those embedded URLs require a future new app build to change; historical packages are not rewritten here. Use the new URLs for current store submission fields and support references. Existing underscore-named legacy repositories are outside this rename and remain unchanged.

GitHub documentation: https://docs.github.com/en/repositories/creating-and-managing-repositories/renaming-a-repository
