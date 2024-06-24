# Animated Splash Screen in Jetpack Compose

Welcome to the repository for the Animated Splash Screen in Jetpack Compose project. This project demonstrates how to create an animated splash screen in a Jetpack Compose application using Kotlin in Android Studio. The splash screen is created using the new Splash Screen API and an animated vector drawable exported from ShapeShifter.io.

## Features

- Jetpack Compose for modern Android UI development.
- Splash Screen API for seamless splash screen integration.
- Animated Vector Drawable (AVD) for smooth and eye-catching animations.

## Getting Started

### Steps to Create the Project

1. **Create a New Project in Android Studio**
   - Open Android Studio and create a new project.
   - Choose an empty activity template and name your project.

2. **Add Splash Screen API Dependency**
   - Open `build.gradle` (app-level) and add the Splash Screen API dependency:
     ```gradle
     dependencies {
         implementation 'androidx.core:core-splashscreen:1.0.0'
     }
     ```
   - Sync the project.

3. **Create a 192x192 Icon in Figma**
   - Design your splash screen icon in Figma which should be under dimensions 192x192.
   - Export the icon as an SVG file.

4. **Animate the Icon Using ShapeShifter.io**
   - Open [ShapeShifter.io](https://shapeshifter.design/).
   - Import the SVG file and create the desired animation.
   - Export the animation as an Animated Vector Drawable (AVD).

5. **Add the AVD to Android Studio**
   - Place the exported AVD file in the `res/drawable` directory of your project.

6. **Create Day and Night Themes**
   - In the `res/values` directory, create two XML files, for example, `splash_theme.xml` and `splash_theme_night.xml`.
   - Define a new theme in each file:
     ```xml
     <!-- splash_theme.xml -->
     <resources>
          <style name="Theme.Splash.AnimatedSplash" parent="Theme.SplashScreen">
              <item name="windowSplashScreenBackground">@color/white</item>
              <item name="windowSplashScreenAnimatedIcon">@drawable/avd_splashscreen</item>
              <item name="windowSplashScreenAnimationDuration">1000</item>
              <item name="postSplashScreenTheme">@style/Theme.Splash</item>
          </style>
      </resources>

     <!-- splash_theme_night.xml -->
     <resources>
          <style name="Theme.Splash.AnimatedSplash" parent="Theme.SplashScreen">
              <item name="windowSplashScreenBackground">@color/white</item>
              <item name="windowSplashScreenAnimatedIcon">@drawable/avd_splashscreen</item>
              <item name="windowSplashScreenAnimationDuration">1000</item>
              <item name="postSplashScreenTheme">@style/Theme.Splash</item>
          </style>
      </resources>
     ```

7. **Update AndroidManifest.xml**
   - Set the new splash screen theme as the theme for your main activity:
     ```xml
     <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Splash" // Here change the theme.
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:theme="@style/Theme.Splash.AnimatedSplash">  // Here change the theme.
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
      </application>
     ```

8. **Initialize Splash Screen in MainActivity**
   - In `MainActivity.kt`, call `installSplashScreen()`:
     ```kotlin
     package com.example.splash

      import android.os.Bundle
      import androidx.activity.ComponentActivity
      import androidx.activity.compose.setContent
      import androidx.activity.enableEdgeToEdge
      import androidx.core.splashscreen.SplashScreen.Companion.installSplashScreen
      import com.example.splash.ui.theme.SplashTheme
      
      class MainActivity : ComponentActivity() {
          override fun onCreate(savedInstanceState: Bundle?) {
              super.onCreate(savedInstanceState)
      
              // Installing Splash Screen :->
              installSplashScreen()
      
              enableEdgeToEdge()
              setContent {
                  SplashTheme {}
              }
          }
      }
     ```


## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

1.> Fork the Project.\
2.> Create your Feature Branch `git checkout -b feature/AmazingFeature`.\
3.> Commit your Changes `git commit -m 'Add some AmazingFeature'`.\
4.> Push to the Branch `git push origin feature/AmazingFeature`.\
5.> Open a Pull Request

## Acknowledgements

- Inspiration from various Android development tutorials and documentation.
## Contact

For questions or feedback, please contact [@Bhavyansh03-tech](https://github.com/Bhavyansh03-tech).
