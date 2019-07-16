# Android App Widget

[Android App widget official documentation](https://developer.android.com/guide/topics/appwidgets)

To start making your first widget, first create your own [`AppWidgetProvider`](https://developer.android.com/reference/android/appwidget/AppWidgetProvider.html) which is simply a helper class that extends a `BroadcastReceiver` to read the intents relevant to a widget. 

```kotlin
class MyWidgetProvider : AppWidgetProvider() {

}
```

Then we will need to declare an info class in xml that will provide the various meta data about the widget such as ability to resize, preview image, layout file, etc.  

```xml
<!-- res/xml/my_widget_info.xml -->
<appwidget-provider xmlns:android="http://schemas.android.com/apk/res/android"
    android:initialLayout="@layout/widget_layout"
    android:minWidth="40dp"
    android:minHeight="40dp"
    android:previewImage="@drawable/ic_baseline_contact_support_24px"
    android:resizeMode="horizontal|vertical"
    android:updatePeriodMillis="86400000"
    android:widgetCategory="home_screen"/>
</appwidget-provider>

```

Open up the `AndroidManifest.xml` to declare your widget

```xml
<receiver android:name=".MyWidgetProvider">
    <intent-filter>
         <action android:name="android.appwidget.action.APPWIDGET_UPDATE"/>
    </intent-filter>

    <meta-data
        android:name="android.appwidget.AppWidgetProvider"
        android:resource="@xml/my_widget_info"/>
</receiver>
```

### Make The Widget Configurable 

If you care to allow the user to configure your widget such as color, size, update period, then we will need to create a configuration `Activity` and declare it in the `AndroidManifest.xml`.

```kotlin
class MyWidgetConfigure : Activity() {

}
```

Then add this activity to the widget info with the `android:configure` tag.

```xml
<!-- res/xml/my_widget_info.xml -->
<appwidget-provider xmlns:android="http://schemas.android.com/apk/res/android"
    ...
    android:configure="com.plusmobileapps.firstwidget.MyWidgetConfigure"
    ... >
</appwidget-provider>
```

## Using Work Manager 

[Enable Java 8 Support](https://developer.android.com/studio/write/java8-support)

[Fix for needing to update kotlin compiler to target 1.8](https://stackoverflow.com/a/48988779)


### Misc Links

[Build an App Widget](https://developer.android.com/guide/topics/appwidgets)

[App Widget Design Guidelines](https://developer.android.com/guide/practices/ui_guidelines/widget_design.html#top_of_page)

[`AppWidgetProvider`](https://developer.android.com/reference/android/appwidget/AppWidgetProvider.html)

[`AppWidgetProviderWindow`](https://developer.android.com/reference/android/appwidget/AppWidgetProviderInfo.html)

[Stack widget app example code](https://android.googlesource.com/platform/development/+/master/samples/StackWidget)

[Example app updating widget from a service](https://android.googlesource.com/platform/development/+/master/samples/Wiktionary/src/com/example/android/wiktionary/WordWidget.java)

[Fix for `JobIntentService` crashing in `AsyncTask`](https://issuetracker.google.com/issues/63622293#comment47) - useful when you use a library that you don't have control over the asynchronous framework

[The CommonsBlog - WorkManager, App Widgets, and the Cost of Side Effects](https://commonsware.com/blog/2018/11/24/workmanager-app-widgets-side-effects.html)