## ImagePicker
A simple library to pick images from the gallery and camera.

[![](https://jitpack.io/v/nguyenhoanglam/ImagePicker.svg)](https://www.jitpack.io/#nguyenhoanglam/ImagePicker)
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-ImagePicker-green.svg?style=true)](https://android-arsenal.com/details/1/4072)

## Screenshot
![111](https://cloud.githubusercontent.com/assets/4979755/17454014/c6b48a5e-5bb2-11e6-9dde-9b8321a569d5.png)

## Download
Add it to your module's build.gradle with:
```java
allprojects {
    repositories {
        maven { url "https://jitpack.io" }
    }
}
```

and:
```java
dependencies {
    compile 'com.github.nguyenhoanglam:ImagePicker:1.0.1'
}
```

## How to use
### Start image picker activity
- Quick call
```java
ImagePicker.create(this)
            .single() // single mode
            .multi() // multi mode (default mode)
            .limit(10) // max images can be selected
            .showCamera(true) // show camera or not (true by default)
            .origin(images) // original selected images, used in multi mode
            .start(REQUEST_CODE_PICKER); // start image picker activity with request code
```                
- Or use traditional Intent
```java
Intent intent = new Intent(this, ImagePickerActivity.class);

intent.putExtra(ImagePickerActivity.INTENT_EXTRA_MODE, ImagePickerActivity.MODE_MULTIPLE);
intent.putExtra(ImagePickerActivity.INTENT_EXTRA_LIMIT, 10);
intent.putExtra(ImagePickerActivity.INTENT_EXTRA_SHOW_CAMERA, true);
intent.putExtra(ImagePickerActivity.INTENT_EXTRA_SELECTED_IMAGES, images);

startActivityForResult(intent, REQUEST_CODE_PICKER);
```        
### Receive result

```java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    if (requestCode == ImagePickerActivity.REQUEST_CODE_PICKER && resultCode == RESULT_OK && data != null) {
        ArrayList<Image> images = data.getParcelableArrayListExtra(ImagePickerActivity.INTENT_EXTRA_SELECTED_IMAGES);
        // do your logic ....
    }
}
```
##Thanks
- Darshan Dorai for [MultipleImageSelect](https://github.com/darsh2/MultipleImageSelect) 
- [Glide](https://github.com/bumptech/glide) for image loading implementation

##License
Copyright 2016 Nguyen Hoang Lam

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
