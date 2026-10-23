# LeaveBy screenshots and videos

Captured from the simulators with the 20 demo city tours seeded (`-SeedDemo`), leaving from Chennai Central, so the
next event is "Start city tour at Marina Beach". Live services: Apple Maps, Open-Meteo weather, Wikimedia photos.
Re-create any set with `scripts/capture.sh` (see docs/CAPTURE.md).

File names: `<device>-<pose or OS>_<orientation>_<screen>.png` and `<device>-<pose>_video_<what happens>.mp4`.

| Device | Pose | Portrait | Landscape | Video (portrait → landscape → portrait, all three tabs) |
|---|---|---|---|---|
| iPhone 17, iOS 26.5 | n/a (not foldable) | `iphone17-ios26_portrait_{next,plan-ahead,day}.png` | `iphone17-ios26_landscape_{next,plan-ahead,day}.png` | `iphone17-ios26_video_rotate-portrait-landscape-portrait_tour.mp4` |
| iPhone Duo, iOS 27.1 | Closed (outer display) | `iphoneduo-closed_portrait_*.png` | `iphoneduo-closed_landscape_*.png` | `iphoneduo-closed_video_rotate-portrait-landscape-portrait_tour.mp4` |
| iPhone Duo, iOS 27.1 | Partially open (127°, inner display) | `iphoneduo-partially-open_{next,plan-ahead,day}.png` (one orientation) |  | `iphoneduo-partially-open_video_tab-tour.mp4` (tabs, no rotation) |
| iPhone Duo, iOS 27.1 | Fully open, held landscape (inner display, wide) |  | `iphoneduo-fully-open-landscape_{next,plan-ahead,day}.png` | `iphoneduo-fully-open-landscape_video_tab-tour.mp4` (tabs, no rotation) |
| iPhone Duo, iOS 27.1 | Fully open, held portrait (inner display, tall; rotated in Device Hub) | `iphoneduo-fully-open-portrait_{next,plan-ahead,day}.png` |  | `iphoneduo-fully-open-portrait_video_tab-tour.mp4` |

Also: `iphoneduo-partially-open_duo-probe_fold-and-camera-regions.png` is the Debug probe in that pose. It reports
the fold band (blue, x 455–495 of a 951 × 669 pt screen) and camera areas (red), and the hinge at 127°.

Notes
- The iPhone 17 and fully-open-portrait videos start on the app. The other three videos were recorded before a
  script fix and begin with about a second of the home screen; re-run `scripts/capture.sh` in that pose to refresh.
- Partially open: on Next, the photo/map column and the plan column meet at the fold, so nothing sits under it.
  Plan ahead's system split view already puts its divider on the fold. The Day list still runs across the fold
  (text stays left of it); that is handled with the Phase 3 Duo layouts.
- When the Duo is open, its inner display ignores the app's rotation request, so open poses are captured in the
  orientation Device Hub shows (`fixed` mode): file names carry no orientation and the video tours the tabs only.
  Both orientations of the open Duo are here: it was rotated in Device Hub between the two captures.
- The Day tab is shown for tomorrow (`-DemoDay 1`), the first day with a demo tour.
- Screenshots are saved upright. Videos record the screen in its native orientation, so landscape parts of a video
  appear turned sideways, as the physical screen would.
- The rotation in the videos is driven by the app's Debug-only demo mode (`-DemoTour`), which asks the system to
  rotate the interface. Folding cannot be scripted in Xcode 27.1's Device Hub, so the open and half-open poses are set by hand.
