---

layout: default
title: Text and Urls
parent: Android
nav_order: 3
permalink: /android/week-3

---

![Alt text](../../assets/images/no-click-1920-removebg-preview.png)

## Redirecting to Link

{% highlight kotlin %}
        val url = "https:gdsc-hitam.github.io";
        startActivity(Intent(Intent.ACTION_VIEW).apply{
            data = Uri.parse(url)
        })
{% endhighlight %}

This block of code stores a link and parses it with an event that can be a click or a transition

### code
{% highlight kotlin %}
package com.example.myapplication

import android.annotation.SuppressLint
import android.content.Intent
import android.net.Uri
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.Toast

class MainActivity2 : AppCompatActivity() {
    @SuppressLint("MissingInflatedId")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main2)


        val click=findViewById<Button>(R.id.bu2)
        click.setOnClickListener {
            Toast.makeText(this, "Going to prev page", Toast.LENGTH_SHORT).show()
            val i = Intent(this, MainActivity::class.java)
            startActivity(i)
        }

        val url = "https:gdsc-hitam.github.io";
        startActivity(Intent(Intent.ACTION_VIEW).apply{
            data = Uri.parse(url)
        })
    }
}
{% endhighlight %}

**xml for link-redirecting**

{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textView"
        android:layout_width="209dp"
        android:layout_height="112dp"
        android:layout_marginStart="51dp"
        android:layout_marginTop="211dp"
        android:layout_marginEnd="51dp"
        android:layout_marginBottom="276dp"
        android:text="YOu are here"
        android:textAppearance="@style/TextAppearance.AppCompat.Large"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.113" />

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

    <com.google.android.material.textfield.TextInputLayout
        android:layout_width="234dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="83dp"
        android:layout_marginTop="123dp"
        android:layout_marginEnd="94dp"
        android:layout_marginBottom="32dp"
        app:layout_constraintBottom_toTopOf="@+id/textView"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>

</androidx.constraintlayout.widget.ConstraintLayout>
{% endhighlight %}

## Text Editing

{% highlight kotlin %}
        showButton.setOnClickListener{
            val text = editText.text
            Toast.makeText(this, text,Toast.LENGTH_SHORT).show()
        }
{% endhighlight %}

This block of code establishes a text field where text can be edited and when any event happens a notification of the text is shown

### code

{% highlight kotlin %}
package com.example.myapplication

import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.Toast

//import android.widget.Toast

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val click=findViewById<Button>(R.id.bu1)
        click.setOnClickListener {
            Toast.makeText(this, "Going to next page", Toast.LENGTH_SHORT).show()
            val i = Intent(this, MainActivity2::class.java)
            startActivity(i)
        }

        val showButton = findViewById<Button>(R.id.Input)
        val editText = findViewById<EditText>(R.id.editText)
        showButton.setOnClickListener{
            val text = editText.text
            Toast.makeText(this, text,Toast.LENGTH_SHORT).show()
        }
    }
}

{% endhighlight %}

**xml for text flashing**

{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/bu1"
        android:layout_width="154dp"
        android:layout_height="67dp"
        android:layout_marginStart="84dp"
        android:layout_marginTop="32dp"
        android:layout_marginEnd="84dp"
        android:text="Press Me"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.494"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.931"
        tools:ignore="MissingConstraints" />

    <Button
        android:id="@+id/Input"
        android:layout_width="88dp"
        android:layout_height="48dp"
        android:layout_marginStart="157dp"
        android:layout_marginTop="105dp"
        android:layout_marginEnd="166dp"
        android:layout_marginBottom="81dp"
        android:text="Edit"
        app:layout_constraintBottom_toTopOf="@+id/bu1"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editText" />

    <EditText
        android:id="@+id/editText"
        android:layout_width="316dp"
        android:layout_height="147dp"
        android:layout_marginStart="47dp"
        android:layout_marginTop="240dp"
        android:layout_marginEnd="48dp"
        android:layout_marginBottom="105dp"
        android:ems="10"
        android:inputType="textPersonName"
        android:text="Name"
        app:layout_constraintBottom_toTopOf="@+id/Input"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
{% endhighlight %}