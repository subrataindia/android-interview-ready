# What is the difference between activity and fragment ?

In Android app development, activities and fragments are two fundamental building blocks used to create user interfaces and manage the application's behavior. Let's explore the differences between activities and fragments, along with examples.

## Activity:

An activity represents a single screen with a user interface. It is a core component of an Android application and serves as the entry point for user interaction. Activities are responsible for handling user input, managing the UI, and coordinating with other components.

Example:

```java
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Your activity initialization code
    }
}
```
In this example, MainActivity extends the AppCompatActivity, and the onCreate method is called when the activity is first created. The setContentView method sets the layout for the activity, which is defined in the XML file (activity_main.xml). This layout contains the UI components for the main screen.

## Fragment:

A fragment represents a portion of a user interface or behavior within an activity. Fragments are used to modularize the UI and create reusable components that can be combined within different activities. Fragments have their own lifecycle and can be added or removed dynamically.

Example:

```java
public class DetailsFragment extends Fragment {
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_details, container, false);
    }
}
```
In this example, DetailsFragment extends the Fragment class, and the onCreateView method is overridden to inflate the layout for the fragment (fragment_details.xml). This layout defines the UI components for the details section.

## Relationship:
Often, activities host fragments, and fragments can be dynamically added, removed, or replaced within an activity. This allows for a more modular and flexible UI design. For example, a tablet layout might use two fragments side by side in landscape mode but switch to a single fragment in portrait mode.

```java
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        if (findViewById(R.id.fragment_container) != null) {
            if (savedInstanceState == null) {
                getSupportFragmentManager().beginTransaction()
                    .add(R.id.fragment_container, new DetailsFragment())
                    .commit();
            }
        }
    }
}
```
In this example, the MainActivity layout (activity_main.xml) includes a container (fragment_container) where the DetailsFragment is dynamically added during the activity's creation.

To summarize, activities represent entire screens with UI and behavior, while fragments represent modular portions of UI or behavior that can be combined within activities. The use of fragments enhances code reuse and facilitates the creation of responsive and flexible user interfaces.
