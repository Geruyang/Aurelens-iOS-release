# Aurelens 0.6.3 build 18 — capture round 2

Captured on 10 September 2026, starting around 15:01 UTC. These are actual app captures, with filenames corresponding to the build 16 reference set.

- iPhone 17 Pro Max **physical device**, iOS 27.0: 14 native screenshots, 1320 × 2868, English and Simplified Chinese; 128-second silent review recording.
- iPad Pro 13-inch (M5) **simulator**, iPadOS Simulator 26.5: 14 native screenshots, 2064 × 2752, English and Simplified Chinese; 144-second silent review recording.
- Both installed apps were verified as 0.6.3 / build 18. No app rebuild was performed for this capture update.
- PNG bytes are identical to the exported XCTest screenshots. Recordings use H.264, have no audio track and retain the original dimensions. Only leading/trailing footage and waiting intervals were cut; the frame rate varies with screen changes.

| 页面 | iPhone 英文 | iPhone 中文 | iPad 模拟器英文 | iPad 模拟器中文 |
| --- | --- | --- | --- | --- |
| 概率预测 | en001.png | cn002.png | en013.png | cn014.png |
| 手动持仓 | en002.png | cn007.png | en012.png | cn016.png |
| 设置 | en003.png | cn003.png | en015.png | cn012.png |
| 全球事件 | en004.png | cn006.png | en017.png | cn013.png |
| 行情图表 | en005.png | cn005.png | en011.png | cn011.png |
| 总览 | en006.png | cn004.png | en016.png | cn017.png |
| 黄金 Agent | en007.png | cn001.png | en014.png | cn015.png |


## Verification and observations

Three navigation/capture runs passed with zero failures: iPhone, initial iPad and iPad retake. This is navigation and capture evidence, not a claim that every physical-device feature was tested. App Store Connect upload and review submission have not been performed.

The initial iPad English capture temporarily used clearly labelled demo data because the live source was unavailable. The final iPad files here come from a complete retake after recovery and waiting for forecast refresh. No demo banner or notification overlay was visible in the final overview screenshots. Values and event lists reflect the capture times and may differ between devices.

Some iPad detail navigation titles are not displayed and some probability cards render with darker backgrounds. Existing local Agent welcome-message history is visible. These actual app-rendering details were retained without retouching. Both devices' original English / U.S. Eastern display settings were restored; holdings and credentials were not edited and paid AI calls were not made.

`SHA256SUMS.txt` covers all 30 media files. `provenance.json` records checksums, capture timestamps and video cut intervals. Complete recordings, device identifiers and detailed XCTest logs remain on the developer's Mac. Capture source and a report are in the private source repository under `tools/capture-build18` and `docs/Capture-0.6.3-build18-round2.md`.

Existing IPA assets, release names, tags and historical filenames remain unchanged. These recordings are review/test materials, not an App Store preview-format certification.
