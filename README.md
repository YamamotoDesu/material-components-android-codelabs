# Codelabs for Material Components for Android (MDC-Android)

[Material Components for Android](https://material.io/components/android/) are modular and customizable UI
components that implement Material Design. This repo houses the source for the suite of [MDC Android - Java](https://material.io/collections/developer-tutorials/#android-java) and [MDC Android - Kotlin](https://material.io/collections/developer-tutorials/#android-kotlin) codelabs.

This repository is structured as branches. You can checkout an individual branch by running `git checkout 101-starter` or the equivalent for the codelab you are following.

There are some simple scripts for maintaining this repository in the `tools/` directory.

## [MDC-101 Android: Material Components (MDC) Basics (Kotlin)](https://codelabs.developers.google.com/codelabs/mdc-101-kotlin)

<img width="351" alt="スクリーンショット 2023-03-23 19 30 42" src="https://user-images.githubusercontent.com/47273077/227176323-74f1d629-5112-4768-98fd-f244771cec9a.png">

MainActivity.kt
```kt
class MainActivity : AppCompatActivity(), NavigationHost {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.shr_main_activity)

        if (savedInstanceState == null) {
            supportFragmentManager
                    .beginTransaction()
                    .add(R.id.container, LoginFragment())
                    .commit()
        }
    }

    /**
     * Navigate to the given fragment.
     *
     * @param fragment       Fragment to navigate to.
     * @param addToBackstack Whether or not the current fragment should be added to the backstack.
     */
    override fun navigateTo(fragment: Fragment, addToBackstack: Boolean) {
        val transaction = supportFragmentManager
                .beginTransaction()
                .replace(R.id.container, fragment)

        if (addToBackstack) {
            transaction.addToBackStack(null)
        }

        transaction.commit()
    }
}
```

LoginFragment.kt
```kt
class LoginFragment : Fragment() {

    override fun onCreateView(
            inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
        // Inflate the layout for this fragment

        // Snippet from "Navigate to the next Fragment" section goes here.

        val view = inflater.inflate(R.layout.shr_login_fragment, container, false)
        return view
    }

    // "isPasswordValid" from "Navigate to the next Fragment" section method goes here
}
```

shr_main_activity.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity" />
```

shr_login_fragment.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/loginPageBackgroundColor"
    tools:context=".LoginFragment">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:clipChildren="false"
        android:clipToPadding="false"
        android:orientation="vertical"
        android:padding="24dp"
        android:paddingTop="16dp">

        <ImageView
            android:layout_width="64dp"
            android:layout_height="64dp"
            android:layout_gravity="center_horizontal"
            android:layout_marginTop="48dp"
            android:layout_marginBottom="16dp"
            app:srcCompat="@drawable/shr_logo"
            android:contentDescription="@string/shr_logo_content_description"  />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center_horizontal"
            android:layout_marginBottom="132dp"
            android:text="@string/shr_app_name"
            android:textAllCaps="true"
            android:textSize="16sp" />

        <!-- Snippet from "Add text fields" section goes here. -->

        <!-- Snippet from "Add buttons" section goes here. -->

    </LinearLayout>
</ScrollView>
```

## 3. Add text fields
<img width="300" alt="スクリーンショット 2023-03-23 20 19 08" src="https://user-images.githubusercontent.com/47273077/227188084-378f0e16-4e92-44af-a8f3-ce2263f9eb2b.png">

```xml
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/loginPageBackgroundColor"
    tools:context=".LoginFragment">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:clipChildren="false"
        android:clipToPadding="false"
        android:orientation="vertical"
        android:padding="24dp"
        android:paddingTop="16dp">

        <ImageView
            android:layout_width="64dp"
            android:layout_height="64dp"
            android:layout_gravity="center_horizontal"
            android:layout_marginTop="48dp"
            android:layout_marginBottom="16dp"
            app:srcCompat="@drawable/shr_logo"
            android:contentDescription="@string/shr_logo_content_description"  />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center_horizontal"
            android:layout_marginBottom="132dp"
            android:text="@string/shr_app_name"
            android:textAllCaps="true"
            android:textSize="16sp" />

        <!-- Snippet from "Add text fields" section goes here. -->
        <com.google.android.material.textfield.TextInputLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="4dp"
            android:hint="@string/shr_hint_username">

            <com.google.android.material.textfield.TextInputEditText
                android:layout_width="match_parent"
                android:layout_height="wrap_content" />

        </com.google.android.material.textfield.TextInputLayout>

        <!-- Snippet from "Add buttons" section goes here. -->
        <com.google.android.material.textfield.TextInputLayout
            android:id="@+id/password_text_input"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="4dp"
            android:hint="@string/shr_hint_password">

            <com.google.android.material.textfield.TextInputEditText
                android:id="@+id/password_edit_text"
                android:layout_width="match_parent"
                android:layout_height="wrap_content" />

        </com.google.android.material.textfield.TextInputLayout>

    </LinearLayout>
</ScrollView>
```
