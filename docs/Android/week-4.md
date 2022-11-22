---

layout: default
title: Firebase
parent: Android
nav_order: 4
permalink: /android/week-4

---

![Firebase](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse3.mm.bing.net%2Fth%3Fid%3DOIP.x8LjUUpPNMwrutD5mee2pwHaDy%26pid%3DApi&f=1&ipt=fa0660ed7ee9f7546b74dbed163f472f162358a8df5d4b0d8c5e06890d296530&ipo=images)

# Login and Registration in Android using Firebase in Kotlin

Firebase is a mobile and web application development platform. It provides services that a web application or mobile application might require. Firebase provides email and password authentication without any overhead of building the backend for user authentication. In this article, we will learn the firebase authentication feature. Using it we can create a Login and Registration page in our app.

## Step by Step Implementation

**Step 1:** First, We need to [connect our project with Firebase](https://www.geeksforgeeks.org/adding-firebase-to-android-app/amp/). For that, we need to go to tools the select firebase option

![step-1](https://media.geeksforgeeks.org/wp-content/uploads/20211129220444/fb01.png)


**Step 2:** Now as we need the Firebase authentication feature, In authentication, we have different options. For this article, we will use **Authenticate using a custom authentication system**. We will click on connect. And add the firebase Authentication SDK to your app.

![step-2](https://media.geeksforgeeks.org/wp-content/uploads/20211206003345/fb02.png)


**Step 3:** Now we will create an XML layout for the Registration Activity.

{% highlight XML %}


<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:id="@+id/linearLayout"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:orientation="vertical"
        android:padding="15dp"
        android:paddingTop="40dp"
        android:paddingBottom="40dp"
        app:layout_constraintBottom_toTopOf="@+id/imageView2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent">

        <EditText
            android:id="@+id/etSEmailAddress"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginLeft="15dp"
            android:layout_marginTop="30dp"
            android:layout_marginRight="15dp"
            android:autofillHints="emailAddress"
            android:ems="10"
            android:hint="@string/email"
            android:inputType="textEmailAddress"
            android:minHeight="48dp"
            android:textColorHint="#757575" />
 

        <EditText
            android:id="@+id/etSPassword"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginLeft="15dp"
            android:layout_marginTop="15dp"
            android:layout_marginRight="15dp"
            android:autofillHints="password"
            android:ems="10"
            android:hint="@string/password"
            android:inputType="textPassword"
            android:minHeight="48dp"
            android:textColorHint="#757575" />
 

        <EditText
            android:id="@+id/etSConfPassword"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginLeft="15dp"
            android:layout_marginTop="15dp"
            android:layout_marginRight="15dp"
            android:autofillHints="password"
            android:ems="10"
            android:hint="@string/confirm_password"
            android:inputType="textPassword"
            android:minHeight="48dp"
            android:textColorHint="#757575"
            tools:ignore="TextContrastCheck" />
 
        <Button
            android:id="@+id/btnSSigned"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="15dp"
            android:background="@drawable/btn_primary"
            android:text="@string/signed" />
 
        <TextView
            android:id="@+id/tvRedirectLogin"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center_horizontal"
            android:layout_margin="10dp"
            android:text="@string/already_have_an_account_login"
            android:textColor="#18206F"
            android:textSize="16sp" />

    </LinearLayout>
 

</androidx.constraintlayout.widget.ConstraintLayout>
{% endhighlight %}


**Step 4**: Now we will code for Registration activity

 

In the Registration activity, We will create a FirebaseAuth object, and using it we will call the **createUserWithEmailAndPassword(email, pass)** function. And check using **addOnCompleteListener()** function, if the response is successful then will display a [Toast](https://www.geeksforgeeks.org/android-what-is-toast-and-how-to-use-it-with-examples/amp/)

{% highlight kotlin %}

package com.ayush.quizapp.activity.activity
import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import android.widget.Toast
import com.ayush.quizapp.R
import com.google.firebase.auth.FirebaseAuth
import com.google.firebase.auth.ktx.auth
import com.google.firebase.ktx.Firebase
 

class SignUpActivity : AppCompatActivity() {
    lateinit var etEmail: EditText
    lateinit var etConfPass: EditText
    private lateinit var etPass: EditText
    private lateinit var btnSignUp: Button
    lateinit var tvRedirectLogin: TextView

      // create Firebase authentication object

    private lateinit var auth: FirebaseAuth  

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_sign_up)

          // View Bindings
        etEmail = findViewById(R.id.etSEmailAddress)
        etConfPass = findViewById(R.id.etSConfPassword)
        etPass = findViewById(R.id.etSPassword)
        btnSignUp = findViewById(R.id.btnSSigned)
        tvRedirectLogin = findViewById(R.id.tvRedirectLogin)

        // Initialising auth object
        auth = Firebase.auth   

        btnSignUp.setOnClickListener {
            signUpUser()
        }
        // switching from signUp Activity to Login Activity
        tvRedirectLogin.setOnClickListener {
            val intent = Intent(this, LoginActivity::class.java)
            startActivity(intent)
        }
    }
 
    private fun signUpUser() {
        val email = etEmail.text.toString()
        val pass = etPass.text.toString()
        val confirmPassword = etConfPass.text.toString()

        // check pass
        if (email.isBlank() || pass.isBlank() || confirmPassword.isBlank()) {
            Toast.makeText(this, "Email and Password can't be blank", Toast.LENGTH_SHORT).show()
            return
        }
        if (pass != confirmPassword) {
            Toast.makeText(this, "Password and Confirm Password do not match", Toast.LENGTH_SHORT)
                .show()
            return
        }

        // If all credential are correct

        // We call createUserWithEmailAndPassword 
          // using auth object and pass the
          // email and pass in it.
        auth.createUserWithEmailAndPassword(email, pass).addOnCompleteListener(this) {
            if (it.isSuccessful) {
                Toast.makeText(this, "Successfully Singed Up", Toast.LENGTH_SHORT).show()
                finish()
            } else {
                Toast.makeText(this, "Singed Up Failed!", Toast.LENGTH_SHORT).show()
            }
        }
    }
}


{% endhighlight %}


**Step 5**:  Now we will design the Login Activity page. Here is the XML code

{% highlight XML %}

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".activity.activity.LoginActivity">

    <LinearLayout
        android:layout_width="0dp"
        android:layout_height="0dp"
        app:layout_constraintBottom_toTopOf="@+id/imageView3"
        android:orientation="vertical"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent">
 
        <EditText
            android:id="@+id/etEmailAddress"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginLeft="15dp"
            android:layout_marginTop="30dp"
            android:layout_marginRight="15dp"
            android:autofillHints="emailAddress"
            android:ems="10"
            android:hint="@string/email"
            android:inputType="textEmailAddress"
            android:minHeight="48dp"
            android:textColorHint="#757575" />
 
        <EditText
            android:id="@+id/etPassword"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginLeft="15dp"
            android:layout_marginTop="15dp"
            android:layout_marginRight="15dp"
            android:autofillHints="password"
            android:ems="10"
            android:hint="@string/password"
            android:inputType="textPassword"
            android:minHeight="48dp"
            android:textColorHint="#757575" />
 
        <Button
            android:id="@+id/btnLogin"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="15dp"
            android:background="@drawable/btn_primary"
            android:text="@string/login" />

        <TextView
            android:id="@+id/tvRedirectSignUp"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="15dp"
            android:gravity="center_horizontal"
            android:text="@string/don_t_have_an_account_sign_in"
            android:textColor="#18206F"
            android:textSize="16sp" />
    </LinearLayout>
</androidx.constraintlayout.widget.ConstraintLayout>

{% endhighlight %}

**[Output](https://media.geeksforgeeks.org/wp-content/uploads/20211129235307/video_2021-11-29_23-50-32.mp4?_=1)**