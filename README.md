Kleinanzeigen ReVanced Hide Ads Fix

Experimental ReVanced patch fix for the Kleinanzeigen Android app.

The official ReVanced "Hide ads" patch stopped working with newer Kleinanzeigen versions because its previous fingerprint matched the old "Liberty.init" implementation.

This project updates the fingerprint to use:

strings("KEY_LIBERTY_REFRESH_INTERVAL")

Tested version

Kleinanzeigen: 2026.33.1
Package: "com.ebay.kleinanzeigen"

Tested successfully on Android 16.

Confirmed working:

* Patching succeeds
* APK installs successfully
* App starts normally
* Kleinanzeigen login works
* Sponsored ads are removed
* Google Ads are removed
* No problems noticed during normal use

Download

Go to the Releases section of this repository and open the latest release:

Kleinanzeigen 2026.33.1 Hide Ads Fix

Under Assets, download the ".rvp" patch bundle.

This repository does not distribute the Kleinanzeigen APK. It contains only the ReVanced patch and the source code required to build it.

Installation

You need ReVanced Manager 2.x.

1. Download the ".rvp" file from the latest GitHub release.
2. Open ReVanced Manager.
3. Open the Patches tab.
4. Tap the button for editing or adding patch sources.
5. Choose Add patches.
6. Choose Select from storage.
7. Select the downloaded ".rvp" file.
8. Select Kleinanzeigen as the app to patch.
9. Use an original Kleinanzeigen 2026.33.1 APK or APK bundle.
10. Select Kleinanzeigen Experimental Patches as the patch source.
11. Enable Hide ads (Kleinanzeigen 2026.33.1 experimental v3).
12. Patch the app.
13. Install the generated APK.
14. Open Kleinanzeigen and log in normally.

The patch has been tested with Kleinanzeigen 2026.33.1. Compatibility with later versions is not guaranteed.

Getting the original Kleinanzeigen app

This repository does not distribute original or modified Kleinanzeigen APK files.

Obtain the original Kleinanzeigen application yourself, for example through APKMirror and the APKMirror downloader supported by ReVanced Manager.

Choose a variant appropriate for your Android device.

Why this patch is necessary

The previous official ReVanced "Hide ads" fingerprint searched for the old "Liberty.init" method.

Newer Kleinanzeigen versions changed this implementation, causing ReVanced to fail with an error similar to:

Hide ads failed:
PatchException: Required value was null

The failure occurred while ReVanced attempted to locate the previous Liberty initialization method.

The updated fingerprint uses the following string:

strings("KEY_LIBERTY_REFRESH_INTERVAL")

This successfully identifies the relevant Liberty advertising initialization method in Kleinanzeigen 2026.33.1.

The existing ReVanced "Hide ads" patch can then return early from this method and prevent the advertising stack from being initialized.

ReVanced upstream contribution

This fix has also been submitted to the official ReVanced Patches project on GitLab:

Merge Request !6977

If this fix is merged into the official ReVanced patches, users should prefer the official ReVanced patch instead of this experimental patch bundle.

Building the patch yourself

The included GitHub Actions workflow is located at:

.github/workflows/build.yml

The workflow automatically:

1. Downloads the official ReVanced Patches source.
2. Replaces the obsolete Kleinanzeigen Hide Ads fingerprint.
3. Builds an Android compatible ".rvp" patch bundle.
4. Publishes the resulting ".rvp" as a GitHub Actions artifact.

You can run the workflow from the Actions section of this repository.

Important

This project does not distribute modified or original Kleinanzeigen APK files.

The patch is experimental and may stop working when Kleinanzeigen changes its application code in a future update.

Only Kleinanzeigen 2026.33.1 has been confirmed working at the time of this release.

This project is not affiliated with, endorsed by, or sponsored by Kleinanzeigen or ReVanced.

License

This project is distributed under the GNU General Public License v3.0.

See the "LICENSE" file for details. 
