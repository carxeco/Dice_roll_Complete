package com.example.diceroll;

import android.content.Intent;
import android.os.Bundle;

import com.google.android.material.floatingactionbutton.FloatingActionButton;
import com.google.android.material.snackbar.Snackbar;

import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;

import android.view.View;
import android.view.Menu;
import android.view.MenuItem;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import java.util.Random;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);

        FloatingActionButton fab = findViewById(R.id.fab);
        fab.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Snackbar.make(view, "Replace with your own action", Snackbar.LENGTH_LONG)
                        .setAction("Action", null).show();
            }
        });
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }

    public void onClick(View v) //Will restarts application, not very efficient but does the job
    {
        switch (v.getId())
        {
            case R.id.button2:
                Intent intent = getIntent();
                finish();
                startActivity(intent);    default:
                break;
        }
    }

    int attemptss;
    int scoress;
    int attempts;
    int scores;
    int number;


    public void on_button_click(View view)
    {
        TextView tv = this.findViewById(R.id.textView2); //sets text to be able to change and output number
        TextView out = this.findViewById(R.id.textView3); //sets text to be editable and produce feedback on answer based on if its right or not
        TextView score = this.findViewById(R.id.textView4); //sets the score to be changable
        TextView attempt = this.findViewById(R.id.textView5); //sets the attempts to be changable
        Random random = new Random(); //replaces old random number
        attempts = attemptss; // set attempts to 0 at start
        scores = scoress; //set score to 00 at start
        number = random.nextInt(6) + 1; // sets lower bound of 1 and upper bound of 6, cannot be 0 as dice have no Zero's
        //while (number == 0) //these lines were removed but i kept for future refernece to see how the code works and why this shouldnt be includedd
        //{
        //  Random n = new Random();
        //    number = n.nextInt (6);
        //  }
        tv.setText(Integer.toString(number)); // changes dice number to string and displays number on screen, changing from "input answer" to "dice output

        EditText user_guess;
        user_guess = findViewById(R.id.user_guess); // choses what box is to be modified
        Integer numbers = Integer.parseInt(user_guess.getText().toString());
        String feedback = ""; //the "feedback" is empty in order to produce a "right" or "wrong" output later when answer is input and compared to dice
        if (number != numbers)  //if statement for correct and wrong answers
        {
            scoress = scores + 0; //score remains unchanged as they have gotten it wrong
            feedback = "Unlucky, try again"; //if answer is wrong it will produce this
        }
        if (number == numbers)
        {
            feedback = "You're right, Well Done!!"; // if answer is right it will produce this message
            scoress = scores + 1; //adds 1 to score ass it correctly guessed the score
        }
        attemptss = attempts + 1; //adds 1 to attempt

        attempt.setText("Attempts: " + attemptss); //presents attempts with new value
        score.setText("Score: " + scoress); //Presents the scores with new value
        out.setText(feedback); // this will produce text on screen
    }

}





    //I INTEGRATED THIS INTO THE CODE ABOVE AFTER THIS CONSTANTLY DIDNT WORK CORRECTLY, CODE IS FINE BUT EXECUTION WASNT STILL LIKE TO KEEP HER FOR CLEAN FUTURE REFERENCE
        //Toast.makeText(this, feedback, Toast.LENGTH_SHORT).show();  //this shows the message in an "error" message type bubble rather than a text box

   // EditText user_guess;

    //public void guesser (View view)
    //{
      //  user_guess = findViewById(R.id.user_guess);
        //Integer numbers = Integer.parseInt(user_guess.getText().toString());
        //String feedback = "";
        //if (number != numbers);
        //{
          //  feedback = "Unlucky, try again";
        //}
        //if (number == numbers)
        //{
          //  feedback = "You're right, Well Done!!";
        //}
        //Toast.makeText(this, feedback, Toast.LENGTH_SHORT).show();
    //}

