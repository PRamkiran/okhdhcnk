4.AIM: Develop an application that shows names as a list and on selecting a name it should show the details of the candidate on the next screen with a “Back” button. If the screen is rotated to landscape mode (width greater than height), then the screen should show list on left fragment and details on right fragment instead of second screen with back button. Use Fragment transactions and Rotation event listener.

XML CODE:
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <ListView
        android:id="@+id/list_names"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">
    </ListView>

</LinearLayout>





JAVA CODE:
package com.example.csbs04;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {
    ListView list_names;
    ArrayList<String> names = new ArrayList<>();

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        names.add("Apple");
        names.add("Orange");
        names.add("Mango");
        list_names = findViewById(R.id.list_names);
        ArrayAdapter<String> names_adapter = new ArrayAdapter<>(MainActivity.this, android.R.layout.simple_list_item_1,names);
        list_names.setAdapter(names_adapter);

        list_names.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {

                if(position ==0)
                {
                    startActivity(new Intent(MainActivity.this,AppleActivity.class));
                }
                else if(position ==1)
                {
                    startActivity(new Intent(MainActivity.this,OrangeActivity.class));
                }
                else
                {
                    startActivity(new Intent(MainActivity.this,MangoActivity.class));
                }
            }
        });

    }
}
