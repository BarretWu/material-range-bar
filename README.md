[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-MaterialRangeBar-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/1272)

MaterialRangeBar
=======
MaterialRangeBar is a fork from https://github.com/edmodo/range-bar that adds some basic material styling, as well as start and end values, values as floats and some other things. It is aiming to mimic this:

http://www.google.com/design/spec/components/sliders.html

It is similar to an enhanced SeekBar widget, though it doesn't make use of the SeekBar. It provides for the selection of a range of values as well as for a single value. The selectable range values are discrete values designated by tick marks; the pin (handle) will snap to the nearest tick mark. This is my first library project, apologies for poor coding, etc etc.

Supported on API Level 12 and above for animations.

![Img](https://github.com/oli107/material-range-bar/blob/master/Screenshots/pin%20expand.gif)

Developers can customize the following attributes (both via XML and programatically):

### Change Log
```
1.4.2 - Added option for rounding status Bar progress using mrb_rangeBar_rounded. Also Implemented seekbar to select the nearest tick, when clicked. Also Fixed Rangebar issue that was causing right pin to move left of left pin when both had same value.
1.4.1 - Small Ui fixes
1.4 - Added mrb_ prefix to all attributes. Also added mrb_selectorBoundaryColor and mrb_selectorBoundarySize attribute.  
1.3 - Stopped pins appearing on initialisation when temporary. Margin correct even if pin radius = 0. PR to correct motion down
1.2 - NPE fixed for movePin
1.1 - Merged pull requests
1.0 - Merged pull requests to fix range bar issues and issues in scrollview, promoted to 1.0 release due to few other PRs.
0.1 - released onto Maven Central. Fixed color pickers in sample. Added ability to set pin color via XML and pin text color via XML or programatically
0.0.1 - 0.0.7 - Initial releases.
```

### Tick Properties
```
mrb_tickStart | float
mrb_tickEnd | float
mrb_tickInterval | float
mrb_tickHeight | dimension
mrb_tickColor | color
```

###  Bar Properties
```
mrb_rangeBar | boolean
mrb_barWeight | dimension
mrb_rangeBarColor | reference or color
mrb_rangeBarPaddingBottom | dimension
mrb_rangeBar_rounded | boolean
mrb_temporaryPins | boolean
mrb_connectingLineWeight | dimension
mrb_connectingLineColor | reference or color
```

### Pin Properties
```
mrb_pinPadding | dimension
mrb_pinRadius | dimension
mrb_pinMinFont | dimension
mrb_pinMaxFont | dimension
mrb_pinColor | reference or color
mrb_pinTextColor | reference or color
mrb_temporaryPins | boolean
```

### Selector Properties
```
mrb_selectorColor | reference or color
mrb_selectorSize | dimension
mrb_selectorBoundaryColor | reference or color
mrb_selectorBoundarySize | dimension
```

### Via runtime only (no XML option)
```
pin indices (the location of the thumbs on the RangeBar)
```

![ScreenShot](https://github.com/oli107/material-range-bar/blob/master/Screenshots/screenshot.png)


Examples
=======

## Layout XML

This is a rangebar with both a lower and upper value
```xml
<com.appyvet.materialrangebar.RangeBar
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="16dp"
        android:layout_marginRight="16dp"
        app:mrb_pinMaxFont="10sp"
        app:mrb_rangeBarPaddingBottom="12dp"
        app:mrb_selectorBoundaryColor="@color/accent"
        app:mrb_selectorBoundarySize="2dp"
        app:mrb_pinTextColor="#ACD123"
        app:mrb_selectorSize="10dp"
        app:mrb_temporaryPins="true"
        app:mrb_tickEnd="10"
        app:mrb_tickInterval="1"
        app:mrb_tickStart="5"/>
```

This is a seekbar with only a single pin (note rangeBar=false)
```xml
<com.appyvet.materialrangebar.RangeBar
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:id="@+id/rangebar"
        android:layout_width="match_parent"
        android:layout_height="72dp"
        app:mrb_rangeBar="false"/>
```

## Adding a rangebar listener
- Add a listener - rangeBar.setOnRangeBarChangeListener which returns left and right index as well as value.
```java
rangebar.setOnRangeBarChangeListener(new RangeBar.OnRangeBarChangeListener() {
            @Override
            public void onRangeChangeListener(RangeBar rangeBar, int leftPinIndex,
                                              int rightPinIndex, String leftPinValue, String rightPinValue) {
            }

        });
```
## Adding a text formatter
Formats the text inside the pin.
- Add a formater - IRangeBarFormatter which will return the value of the current text inside of the pin
- Transform string s into any string you want and return the newly formated string. 
```java
rangebar.setFormatter(new IRangeBarFormatter() {
            @Override
            public String format(String s) {
            // Transform the String s here then return s
                return null;
            }
        });
```

Plan for Future
=======
- Better documentation.
- Properly implement Map of strings to each value

Demo
=======
[Get it from the Google Play Store](https://play.google.com/store/apps/details?id=com.appyvet.rangebarsample)


How to Use
=======

**In your project build.gradle. Add the following lines**
```groovy
allprojects {
    repositories {
        jcenter()
    }
}
```
- Note: Don't put the above lines inside the buildscript block.

**In your app build.gradle. Add the following lines**

```groovy
dependencies {
    implementation 'com.appyvet:materialrangebar:1.4.2'
}
```


**if you are already using android support library inside your project and run into multiple version issues related to android support library then modify the gradle path like this**
```groovy
dependencies {
    compile ('com.appyvet:materialrangebar:1.4.2') {
            exclude module: 'support-compat'
    }
}
```

Contribution
=======
You are always welcome to contribute and help us mantain the library. 


License
=======

    Copyright 2015  AppyVet, Inc.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
