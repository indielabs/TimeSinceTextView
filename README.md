# TimeSinceTextView
## With Arabic language support

This is a subclass of android.widget.TextView that exposes a method `setDate()` which accepts a `long` Unix timestamp or `java.util.Date`. The view converts the date into a String which describes the date in terms of time since that timestamp. For example, if the current timestamp is Unix 1453503166 and we call `timeSinceTextView.setDate(1453503116)`, "50 seconds ago" is displayed.


[![](https://jitpack.io/v/indielabs/TimeSinceTextView.svg)](https://jitpack.io/#indielabs/TimeSinceTextView)

This fork support Arabic language, and follows the language plurals e.g.:

```xml
    <plurals name="tstv_timespan_in_hours">
        <item quantity="zero">الآن</item>
        <item quantity="one">بعد ساعة</item>
        <item quantity="two">بعد ساعتين</item>
        <item quantity="few">بعد %d ساعات</item>
        <item quantity="many">بعد %d ساعة</item>
    </plurals>
```

## Comparison to DateUtils.getRelativeTimeSpanString

I actually wrote this library before I knew about [DateUtils.getRelativeTimeSpanString](http://developer.android.com/reference/android/text/format/DateUtils.html#getRelativeDateTimeString), but the output is actually quite a bit different. The DateUtils implementation should return localized text and allows for customizable flags. See [here](Comparison.md) for a comparison of the output of different time stamps.

## Usage

Simply declare a `TimeSinceTextView` in XML or create one in code.

```xml
<com.ddiehl.timesincetextview.TimeSinceTextView
  android:id="@+id/timestamp"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content" />
```

Then call `setDate(Date)` or `setDate(long)` with a Unix timestamp, and the text will be automatically generated and set to the view.

```java
((TimeSinceTextView) findViewById(R.id.timestamp)).setDate(1452827942);
```



The class `TimeSince` also contains static methods which can be used to retrieve a relative timestamp string without an instance of `TimeSinceTextView`.

## Add to your project

[![](https://jitpack.io/v/indielabs/TimeSinceTextView.svg)](https://jitpack.io/#indielabs/TimeSinceTextView)

```gradle
repositories {
    maven { url "https://jitpack.io" }
}
dependencies {
  compile 'com.github.indielabs:TimeSinceTextView:1.+'
}
```

![Screenshot](/screenshots/1453502946.png)

