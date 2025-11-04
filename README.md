# Ex.No: 06 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Design xml files for all operations such as blink, rotate, move, slide, zoom, fade.

Step 6: Display the button operations in MainActivity file.

Step 7: Save and run the application


## PROGRAM:
```
/*
Program to display animation operation”.
Developed by : MELKIN SAM.D
Registeration Number : 212223220056
*/
```
MAIN_ACTIVITY.JAVA:
```
package com.example.animation;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;
    Button blinkBtn, fadeBtn, moveBtn, rotateBtn, slideBtn, zoomBtn, stopBtn;
    Animation currentAnimation;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);
        blinkBtn = findViewById(R.id.blinkBtn);
        fadeBtn = findViewById(R.id.fadeBtn);
        moveBtn = findViewById(R.id.moveBtn);
        rotateBtn = findViewById(R.id.rotateBtn);
        slideBtn = findViewById(R.id.slideBtn);
        zoomBtn = findViewById(R.id.zoomBtn);
        stopBtn = findViewById(R.id.stopBtn);

        blinkBtn.setOnClickListener(v -> startAnimation(R.anim.blink));
        fadeBtn.setOnClickListener(v -> startAnimation(R.anim.fade));
        moveBtn.setOnClickListener(v -> startAnimation(R.anim.move));
        rotateBtn.setOnClickListener(v -> startAnimation(R.anim.rotate));
        slideBtn.setOnClickListener(v -> startAnimation(R.anim.slide));
        zoomBtn.setOnClickListener(v -> startAnimation(R.anim.zoom));

        stopBtn.setOnClickListener(v -> stopAnimation());
    }

    private void startAnimation(int animRes) {
        stopAnimation(); // stop if already animating
        currentAnimation = AnimationUtils.loadAnimation(this, animRes);
        imageView.startAnimation(currentAnimation);
    }

    private void stopAnimation() {
        if (currentAnimation != null) {
            currentAnimation.cancel();
            imageView.clearAnimation();
        }
    }
}

```
ACTIVITY_MAIN.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:orientation="vertical"
        android:gravity="center"
        android:padding="20dp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <ImageView
            android:id="@+id/imageView"
            android:layout_width="200dp"
            android:layout_height="200dp"
            android:layout_marginBottom="30dp"
            android:src="@drawable/csk" />

        <Button
            android:id="@+id/blinkBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Blink" />

        <Button
            android:id="@+id/fadeBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Fade" />

        <Button
            android:id="@+id/moveBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Move" />

        <Button
            android:id="@+id/rotateBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Rotate" />

        <Button
            android:id="@+id/slideBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Slide" />

        <Button
            android:id="@+id/zoomBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Zoom" />

        <Button
            android:id="@+id/stopBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Stop Animation"
            android:backgroundTint="#FF5252"
            android:textColor="#FFFFFF"
            android:layout_marginTop="10dp" />
    </LinearLayout>
</ScrollView>

```
BLINK.XML
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="500"
    android:fromAlpha="0.0"
    android:toAlpha="1.0"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```
ROTATE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<rotate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromDegrees="0"
    android:toDegrees="360"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1500"
    android:repeatCount="infinite" />

```
FADE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromAlpha="0.0"
    android:toAlpha="1.0"
    android:duration="2000"
    android:repeatCount="infinite"
    android:repeatMode="reverse" />

```
MOVE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXDelta="0%"
    android:toXDelta="75%"
    android:duration="1000"
    android:repeatCount="infinite"
    android:repeatMode="reverse" />

```
SLIDE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromYDelta="100%"
    android:toYDelta="0%"
    android:duration="1000"
    android:repeatCount="infinite"
    android:repeatMode="reverse" />

```
ZOOM.XML
```
<?xml version="1.0" encoding="utf-8"?>
<scale xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXScale="1.0"
    android:toXScale="1.5"
    android:fromYScale="1.0"
    android:toYScale="1.5"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1000"
    android:repeatCount="infinite"
    android:repeatMode="reverse" />

```


## OUTPUT
<img width="601" height="964" alt="image" src="https://github.com/user-attachments/assets/e21bd442-a226-4fab-a1f1-ec986cacce0e" />
<img width="578" height="940" alt="image" src="https://github.com/user-attachments/assets/51530186-1ce8-4d34-b33f-fda23e0460de" />
<img width="588" height="974" alt="image" src="https://github.com/user-attachments/assets/04e111bb-b7e9-44f9-9d64-8e25587d8507" />
<img width="598" height="971" alt="image" src="https://github.com/user-attachments/assets/be3100d0-901a-45c7-99b9-4017d5b655f7" />
<img width="603" height="971" alt="image" src="https://github.com/user-attachments/assets/2647dea3-9bf1-4bca-8fed-f9706011d5ee" />
<img width="602" height="972" alt="image" src="https://github.com/user-attachments/assets/4bbfb8fb-71b3-4939-85bf-c16e87039201" />





## RESULT
Thus a Simple Android Application to add animations: Move,blink,fade,clockwise,zoom,slide operations using Android Studio is developed and executed successfully.
