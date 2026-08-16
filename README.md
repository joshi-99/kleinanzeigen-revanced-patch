# Kleinanzeigen ReVanced Hide Ads Fix

Experimental ReVanced patch fix for the Kleinanzeigen Android app.

The official ReVanced `Hide ads` patch stopped matching newer Kleinanzeigen versions because the previous fingerprint targeted the old `Liberty.init` implementation.

This repository builds a modified ReVanced patch bundle using a fingerprint based on:

```kotlin
strings("KEY_LIBERTY_REFRESH_INTERVAL")
