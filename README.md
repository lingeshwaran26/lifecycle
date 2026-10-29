# Practical 3: Activity Lifecycle and Logcat Analysis

Develop an Android application demonstrating complete Activity Lifecycle methods and analyze execution using Logcat.

---

## Project Overview

* **Project Name:** logcat
* **Template:** Empty Views Activity
* **Language:** Java
* **Package Name:** `com.example.logact`

---

## 1. Java Source Code

### `MainActivity.java`
**Path:** `app > java > com > example > logact > MainActivity.java`

```java
package com.example.logact;

import android.os.Bundle;
import android.util.Log;
import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.d("on start invoked", "on started");
    }

    @Override
    protected void onPostResume() {
        super.onPostResume();
        Log.d("on resume invoked", "on resume");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.d("on pause invoked", "on pause");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.d("on stop invoked", "on stopped");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d("on destroy invoked", "on destroy");
    }
}
```

---

## 2. Layout XML File

### `activity_main.xml`
**Path:** `app > res > layout > activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout android:gravity="center" android:layout_height="match_parent" android:layout_width="match_parent" android:orientation="vertical" android:padding="16dp" xmlns:android="[http://schemas.android.com/apk/res/android](http://schemas.android.com/apk/res/android)">

    <TextView android:layout_height="wrap_content" android:layout_width="wrap_content" android:text="Activity Lifecycle Demo" android:textSize="20sp" android:textStyle="bold"/>

    <TextView android:layout_height="wrap_content" android:layout_marginTop="8dp" android:layout_width="wrap_content" android:text="Open Logcat in Android Studio to observe state transitions." android:textSize="14sp"/>

</LinearLayout>
```

---

## 3. Manifest File

### `AndroidManifest.xml`
**Path:** `app > manifests > AndroidManifest.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="[http://schemas.android.com/apk/res/android](http://schemas.android.com/apk/res/android)"
    package="com.example.logact">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="logcat"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.AppCompat.Light.DarkActionBar">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>

</manifest>
```

---

## 4. Execution & Logcat Analysis Instructions

1. **Run the App:** Click the green **Play (Run)** button at the top toolbar in Android Studio.
2. **Open Logcat:** Click the **Logcat** tab at the bottom toolbar (or press `Alt + 6` / `Cmd + 6`).
3. **Filter Logs:** In the search/filter bar of Logcat, type `invoked` or filter by tag.
4. **Lifecycle Verification Steps:**
   * **App Launch:** Observe `on started` and `on resume` in the console.
   * **Press Home Button:** Observe `on pause` followed by `on stopped`.
   * **Re-open App:** Observe `on started` and `on resume`.
   * **Press Back Button:** Observe `on pause`, `on stopped`, and `on destroy`.
