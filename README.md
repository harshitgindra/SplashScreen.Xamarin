# Splash Screen.Xamarin
This project is an example to have a custom Launch Screen or Splash Screen to your Xamarin Forms app for Android and iOS.

## Getting Started
To implement a splash screen, we do not need any additional componenets or nuget packages. You can check out this **[video tutorial](https://youtu.be/dzS9v_86ot4)** to see the code in action

## Android Implementation

### First step
Create/import the splash images into the solution. Please check the following **[link](https://developer.android.com/guide/practices/screens_support)** to understand the image size requirments for different screen sizes for Android.

### Second step
Create a new xml file **splash_screen.xml** to display image 

```
<?xml version="1.0" encoding="UTF-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item>
        <bitmap android:src="@drawable/background" android:tileMode="disabled" android:gravity="fill" />
    </item>
</layer-list>
```

### Third Step
Create a new theme/style that will render the launch image. Add the following lines to your **styles.xml**
```
<style name="MyTheme.Splash" parent="Theme.AppCompat.Light">
        <item name="android:windowBackground">@drawable/splash_screen</item>
        <item name="android:windowNoTitle">true</item>
</style>
```
### Forth Step
Create a new Activity **SplashActivity.cs** that will launch the splash screen using the newly added theme

```
 [Activity(Theme = "@style/MyTheme.Splash", MainLauncher = true, NoHistory = true)]
    public class SplashActivity : AppCompatActivity
    {
        public override void OnCreate(Bundle savedInstanceState, PersistableBundle persistentState)
        {
            base.OnCreate(savedInstanceState, persistentState);
        }

        protected override void OnResume()
        {
            base.OnResume();
            var intent = new Intent(this, typeof(MainActivity));
            if (Intent.Extras != null)
            {
                intent.PutExtras(Intent.Extras);
            }
            StartActivity(intent);
        }
    }
```

### Fifth Step
Update **MainActivity.cs** class and set the property **MainLauncher = false**
```
[Activity(Label = "SplashScreen", Icon = "@mipmap/icon", Theme = "@style/MainTheme", MainLauncher = false, ConfigurationChanges = ConfigChanges.ScreenSize | ConfigChanges.Orientation)]
```
All the necessary changes are done. Run the app and verify the changes.
 
## iOS Implementation
Please refer to the **[video link](https://youtu.be/dzS9v_86ot4)** to understand how to implement for iOS devices.
 
## License
This project is open source.

##### Thank you
