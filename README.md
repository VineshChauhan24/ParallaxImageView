<p align="center">
    <img src="logo/logo_ldpi.png"/>
</p>

# Android Parallax Image View
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/1f64b868d7d948f6aaf9544607e16a48)](https://app.codacy.com/app/abdularis/ParallaxImageView?utm_source=github.com&utm_medium=referral&utm_content=abdularis/ParallaxImageView&utm_campaign=Badge_Grade_Dashboard)
[![](https://jitpack.io/v/abdularis/ParallaxImageView.svg)](https://jitpack.io/#abdularis/ParallaxImageView)
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-ParallaxImageView-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/6906)
[![API](https://img.shields.io/badge/API-14%2B-yellowgreen.svg?style=flat)](https://android-arsenal.com/api?level=14)

Creates effect such as vertical parallax, horizontal parallax etc. on android ImageView when it's being vertically or horizontally scrolled (moving) on the screen.

References:
-   [https://abdularis.com/2018/06/06/scroll_parallax_image_view.html](https://abdularis.com/2018/06/06/scroll_parallax_image_view.html)
-   [https://medium.com/@abdularis/android-custom-view-tutorial-scroll-parallax-image-view-2140ac292ecb](https://medium.com/@abdularis/android-custom-view-tutorial-scroll-parallax-image-view-2140ac292ecb)

## Screenshot
![](screenshots/screenshot_1.gif)

## Setup
-   **Step 1** Add repository into root build.gradle

~~~gradle
allprojects {
    repositories {
    ...
    maven {
        url 'https://jitpack.io' }
    }
}
~~~

-   **Step 2** Add library dependency into app build.gradle

~~~gradle
dependencies {
    implementation 'com.github.abdularis:parallaximageview:1.1'
}
~~~

## Usage
-   Create vertical parallax image view
~~~xml
<com.github.abdularis.piv.VerticalScrollParallaxImageView
    android:id="@+id/image_view"
    android:layout_width="200dp"
    android:layout_height="170dp"
    android:src="@drawable/img1"/>
~~~

-   Create Horizontal parallax image view
~~~xml
<com.github.abdularis.piv.HorizontalScrollParallaxImageView
    android:id="@+id/image_view"
    android:layout_width="200dp"
    android:layout_height="170dp"
    android:src="@drawable/img1"/>
~~~

-   Create and customize effect on your own
~~~xml
<com.github.abdularis.piv.ScrollTransformImageView
    android:id="@+id/image_view"
    android:layout_width="200dp"
    android:layout_height="170dp"
    android:src="@drawable/img1"/>
~~~

In the java/kotlin code you can set the effect (transformer) manually. There are three built-in effect classes, VerticalParallaxTransformer, HorizontalParallaxTransformer, HorizontalScaleTransformer.

Java code
~~~java
ScrollTransformImageView img = findViewById(R.id.image_view);

// create horizontal scale effect
img.setViewTransformer(new HorizontalScaleTransformer())

// create vertical or horizontal parallax effect manually
// img.setViewTransformer(new VerticalParallaxTransformer())
// img.setViewTransformer(new HorizontalParallaxTransformer())
//
// the VerticalParallaxImageView or HorizontalParallaxImageView are nothing but the ScrollTransformImageView with coresponding parallax effect
~~~

You can create your own custom effect by extending ViewTransformer.
~~~java
public class CustomTransformer extends ViewTransformer {
    @Override
    public void onAttached(@NotNull ScrollTransformImageView view) {
        // do something when this transformer is set into image view
    }

    @Override
    public void onDetached(@NotNull ScrollTransformImageView view) {
        // do something when this transformer is remove from image view
    }

    @Override
    public void apply(@NotNull ScrollTransformImageView view, @NotNull Canvas canvas, int viewX, int viewY) {
        // do transformation effect or so, this would be called everytime image view move/scrolled
    }
}
~~~

## License

MIT License
