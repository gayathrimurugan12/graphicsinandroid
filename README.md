
# Ex.No:12 Design an application that draws basic graphical primitives on the screen.


## AIM:

To create and design an android application that draws basic graphical primitives on the screen using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “graphical″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Draw basic object details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to create and design an android application that draws basic graphical primitives on the screen.
Developed by: Gayathri M
Registeration Number : 212223220024
*/
```
## MainActivity.java
```
package com.example.graphicsdemo;

import android.app.Activity;
import android.os.Bundle;

public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        setContentView(new GraphicsView(this));
    }
}

```
## GraphicsView
```
package com.example.graphicsdemo;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.RectF;
import android.view.View;

public class GraphicsView extends View {

    private Paint paint;

    public GraphicsView(Context context) {
        super(context);

        paint = new Paint(Paint.ANTI_ALIAS_FLAG);
        paint.setStrokeWidth(8);
        paint.setStrokeCap(Paint.Cap.ROUND);

        // Enable soft shadows
        setLayerType(View.LAYER_TYPE_SOFTWARE, null);
    }

    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);

        float w = getWidth();
        float h = getHeight();

        // Background
        canvas.drawColor(Color.rgb(250, 247, 242));

        // -------------------------------
        // TITLE
        // -------------------------------
        paint.clearShadowLayer();
        paint.setStyle(Paint.Style.FILL);
        paint.setColor(Color.rgb(55, 55, 55));
        paint.setTextAlign(Paint.Align.CENTER);
        paint.setTextSize(48);

        canvas.drawText("SHAPE GALLERY", w / 2, 100, paint);

        paint.setTextSize(22);
        paint.setColor(Color.rgb(120, 120, 120));

        canvas.drawText("Simple • Creative • Geometric",
                w / 2, 140, paint);


        // -------------------------------
        // CIRCLE CARD
        // -------------------------------
        drawCard(canvas, 50, 190, w / 2 - 20, 470);

        paint.setShadowLayer(12, 4, 4, Color.LTGRAY);
        paint.setStyle(Paint.Style.FILL);
        paint.setColor(Color.rgb(174, 216, 230));

        canvas.drawCircle(
                w / 4,
                315,
                65,
                paint
        );

        drawLabel(canvas, "CIRCLE", w / 4, 425);


        // -------------------------------
        // RECTANGLE CARD
        // -------------------------------
        drawCard(canvas, w / 2 + 20, 190, w - 50, 470);

        paint.setShadowLayer(12, 4, 4, Color.LTGRAY);
        paint.setColor(Color.rgb(205, 183, 225));

        RectF rectangle = new RectF(
                w / 2 + 55,
                260,
                w - 85,
                370
        );

        canvas.drawRoundRect(
                rectangle,
                20,
                20,
                paint
        );

        drawLabel(canvas, "RECTANGLE", w * 0.75f, 425);


        // -------------------------------
        // SQUARE CARD
        // -------------------------------
        drawCard(canvas, 50, 500, w / 2 - 20, 780);

        paint.setShadowLayer(12, 4, 4, Color.LTGRAY);
        paint.setColor(Color.rgb(245, 220, 145));

        canvas.drawRect(
                w / 4 - 65,
                570,
                w / 4 + 65,
                700,
                paint
        );

        drawLabel(canvas, "SQUARE", w / 4, 740);


        // -------------------------------
        // LINE CARD
        // -------------------------------
        drawCard(canvas, w / 2 + 20, 500, w - 50, 780);

        paint.setShadowLayer(8, 3, 3, Color.LTGRAY);
        paint.setStyle(Paint.Style.STROKE);
        paint.setStrokeWidth(12);
        paint.setStrokeCap(Paint.Cap.ROUND);
        paint.setColor(Color.rgb(170, 210, 175));

        canvas.drawLine(
                w / 2 + 70,
                635,
                w - 75,
                635,
                paint
        );

        drawLabel(canvas, "LINE", w * 0.75f, 740);
    }


    // ----------------------------------
    // CARD METHOD
    // ----------------------------------
    private void drawCard(
            Canvas canvas,
            float left,
            float top,
            float right,
            float bottom) {

        paint.clearShadowLayer();
        paint.setStyle(Paint.Style.FILL);
        paint.setColor(Color.WHITE);

        canvas.drawRoundRect(
                new RectF(left, top, right, bottom),
                30,
                30,
                paint
        );
    }


    // ----------------------------------
    // LABEL METHOD
    // ----------------------------------
    private void drawLabel(
            Canvas canvas,
            String text,
            float x,
            float y) {

        paint.clearShadowLayer();
        paint.setStyle(Paint.Style.FILL);
        paint.setColor(Color.rgb(70, 70, 70));
        paint.setTextAlign(Paint.Align.CENTER);
        paint.setTextSize(24);

        canvas.drawText(text, x, y, paint);
    }
}
```
## Activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>

<ScrollView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#FAF7F2">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="20dp">

        <!-- TITLE -->
        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="✦ SHAPE GALLERY ✦"
            android:textSize="28sp"
            android:textStyle="bold"
            android:textColor="#373737"
            android:gravity="center"
            android:layout_marginTop="20dp"/>

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Simple • Creative • Geometric"
            android:textSize="14sp"
            android:textColor="#888888"
            android:gravity="center"
            android:layout_marginTop="5dp"
            android:layout_marginBottom="25dp"/>


        <!-- ROW 1 -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="220dp"
            android:orientation="horizontal">

            <!-- CIRCLE -->
            <LinearLayout
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:orientation="vertical"
                android:gravity="center"
                android:background="#FFFFFF"
                android:layout_margin="7dp">

                <View
                    android:layout_width="100dp"
                    android:layout_height="100dp"
                    android:background="#AED8E6"/>

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="●  CIRCLE"
                    android:textSize="17sp"
                    android:textStyle="bold"
                    android:textColor="#464646"
                    android:layout_marginTop="15dp"/>

            </LinearLayout>


            <!-- RECTANGLE -->
            <LinearLayout
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:orientation="vertical"
                android:gravity="center"
                android:background="#FFFFFF"
                android:layout_margin="7dp">

                <View
                    android:layout_width="130dp"
                    android:layout_height="75dp"
                    android:background="#CDB7E1"/>

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="▰  RECTANGLE"
                    android:textSize="17sp"
                    android:textStyle="bold"
                    android:textColor="#464646"
                    android:layout_marginTop="20dp"/>

            </LinearLayout>

        </LinearLayout>


        <!-- ROW 2 -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="220dp"
            android:orientation="horizontal">

            <!-- SQUARE -->
            <LinearLayout
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:orientation="vertical"
                android:gravity="center"
                android:background="#FFFFFF"
                android:layout_margin="7dp">

                <View
                    android:layout_width="100dp"
                    android:layout_height="100dp"
                    android:background="#F5DC91"/>

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="■  SQUARE"
                    android:textSize="17sp"
                    android:textStyle="bold"
                    android:textColor="#464646"
                    android:layout_marginTop="15dp"/>

            </LinearLayout>


            <!-- LINE -->
            <LinearLayout
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:orientation="vertical"
                android:gravity="center"
                android:background="#FFFFFF"
                android:layout_margin="7dp">

                <View
                    android:layout_width="140dp"
                    android:layout_height="8dp"
                    android:background="#AAD2AF"/>

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="—  LINE"
                    android:textSize="17sp"
                    android:textStyle="bold"
                    android:textColor="#464646"
                    android:layout_marginTop="30dp"/>

            </LinearLayout>

        </LinearLayout>


        <!-- FOOTER -->
        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="4 Basic Primitives • Android Graphics"
            android:textSize="13sp"
            android:textColor="#999999"
            android:gravity="center"
            android:layout_marginTop="20dp"
            android:layout_marginBottom="20dp"/>

    </LinearLayout>

</ScrollView>
```

## OUTPUT


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c17ec31b-e1ec-489a-9fda-f93d8241294b" />


## RESULT
Thus a Simple Android Application to create and design an android application that draws basic graphical primitives on the screen using Android Studio is developed and executed successfully.
