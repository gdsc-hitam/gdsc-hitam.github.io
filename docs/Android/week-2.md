---
layout: default
title: UI Interface
parent: Android
nav_order: 3
---

# Create a project

Android Studio makes it easy to create Android apps for various form factors, such as handsets, tablets, TV, and Wear devices. This page shows you how to start a new Android app project or import an existing project.

If you don't have a project opened, Android Studio shows the Welcome screen, where you can create a new project by clicking **Start a new Android Studio project**.

If you do have a project opened, create a new project by selecting **File > New > New Project** from the main menu.

You then see the **Create New Project** wizard, which lets you choose the type of project you want to create and populates with code and resources to get you started. This page guides you through creating a new project using the **Create New Project** wizard.

## Choose your Project

In the **Choose your project** screen that appears, you can select the type of project you want to create from categories of device form factors, which are shown as tabs near the top of the wizard. For example, figure 1 shows a project with a basic Android Activity for a phone and tablet selected.

!["Image"](https://developer.android.com/static/studio/images/projects/new-project-wizard-choose_2x.png)

By selecting the type of project you want to create, Android Studio can include sample code and resources to help you get started.

After you make a selection, click **Next**.

## Configure the Project

The next step is to configure some settings and create your new project

!["Image"](https://developer.android.com/static/studio/images/projects/new-project-wizard-configure-2x.png)


1. Specify the **Name** of your project.
2. Specify the **Package name**. By default, this package name becomes your project's namespace (used to access your project resources) and your project's application ID (used as the ID for publishing). To learn more, see Configure the app module.
3. Specify the **Save location** where you want to locally store your project.
4. Select the **Language** you want Android Studio to use when creating sample code for your new project. Keep in mind, you are not limited to using only that language in the project.
5. Select the **Minimum API level** you want your app to support. When you select a lower API level, your app can't use as many modern Android APIs. However, a larger percentage of Android devices are able to run your app. The opposite is true when selecting a higher API level. If you want to see more data to help you decide, click **Help me choose**.

6. When you're ready to create your project, click **Finish**.

## What we did!!

So after your project is created the directory structure should be have the template code.

The details of the UI were been discussed in the sessions so we are just going to provide the code here of the week-2 session [here](https://github.com/GDSCHITAM/week-2/commit/46e583a3ba66453d4e579e22801a133e1860a9c5).

AndroidManifest.xml
{: .text-purple-200}
{% highlight XML %}
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.MyApplication"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity2"
            android:exported="false">
            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
    </application>

</manifest>
{% endhighlight %}

---

java/com/example/myapplication/MainActivity.kt
{: .text-purple-200}

{% highlight kotlin %}

package com.example.myapplication

import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
//import android.widget.Toast

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val secondActButton = findViewById<Button>(R.id.bu1)
        secondActButton.setOnClickListener {
            val i = Intent(this, MainActivity2::class.java)
            startActivity(i)
        }
    }
}

{% endhighlight %}

---

java/com/example/myapplication/MainActivity2.kt
{: .text-purple-200}

{% highlight kotlin %}
package com.example.myapplication

import android.annotation.SuppressLint
import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button

class MainActivity2 : AppCompatActivity() {
    @SuppressLint("MissingInflatedId")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main2)


        val secondActButton = findViewById<Button>(R.id.bu2)
        secondActButton.setOnClickListener {
            val i = Intent(this, MainActivity::class.java)
            startActivity(i)
        }
    }
}
{% endhighlight%}

---

res/layout/activity_main.xml
{: .text-purple-200}

{% highlight XML %}

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/bu1"
        android:layout_width="243dp"
        android:layout_height="141dp"
        android:layout_marginStart="84dp"
        android:layout_marginTop="295dp"
        android:layout_marginEnd="84dp"
        android:layout_marginBottom="295dp"
        android:text="Press Me"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="MissingConstraints" />

</androidx.constraintlayout.widget.ConstraintLayout>

{% endhighlight %}

---

res/layout/activity_main2.xml
{: .text-purple-200}

{% highlight XML %}
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textView"
        android:layout_width="309dp"
        android:layout_height="244dp"
        android:layout_marginStart="51dp"
        android:layout_marginTop="211dp"
        android:layout_marginEnd="51dp"
        android:layout_marginBottom="276dp"
        android:text="YOu are here"
        android:textAppearance="@style/TextAppearance.AppCompat.Large"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/bu2"
        android:layout_width="141dp"
        android:layout_height="86dp"
        android:layout_marginStart="136dp"
        android:layout_marginTop="22dp"
        android:layout_marginEnd="135dp"
        android:layout_marginBottom="168dp"
        android:text="Button"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />
</androidx.constraintlayout.widget.ConstraintLayout>
{% endhighlight %}

---