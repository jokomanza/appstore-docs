# appstore-docs

## Download
Untuk download installer menggunakan service <br>



Untuk mengecek apakah ada update atau tidak, buat sebuah service yang selalu 
mgecek semua apliaksi yang terinstall, dan jika ada update, membuat broadcast 
tentang update yang ditemukan ke semua fragment yang membutuhkannya.

## In-app Update
Buat library <br>

```groovy
implementation("com.quick.android.store:app-update:1.0.0")

implementation("com.quick.android.store:app-update-ktx:1.0.0")

```

```kotlin
val appUpdateManager = AppUpdateManagerFactory.create(context)

// Returns an intent object that you use to check for an update.
val appUpdateInfoTask = appUpdateManager.appUpdateInfo

// Checks that the platform will allow the specified type of update.
appUpdateInfoTask.addOnSuccessListener { appUpdateInfo ->
    if (appUpdateInfo.updateAvailability() == UpdateAvailability.UPDATE_AVAILABLE
        // This example applies an immediate update. To apply a flexible update
        // instead, pass in AppUpdateType.FLEXIBLE
        && appUpdateInfo.isUpdateTypeAllowed(AppUpdateType.IMMEDIATE)
    ) {
        // Request the update.
    }
}
```

