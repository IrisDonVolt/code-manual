# Login/Signup 

## Step 1: create onclicklistener for the login/signup button
  
    /* check if user already logged in 
    if yes, directly go to the required activity
    if no, then go to the signup/login page and do the required stuff */ 
    
    if (FirebaseAuth.getInstance().getCurrentUser() != null) {
      startActivity(...); 
      finish(); 
    }
    
    //using the same button for signup and login, changing UI/function 
    //based on conditions 
    btnSubmit.setOnClickListener(new View.OnClickListener() {
      @Override 
      public void onClick(View v) {
        if (isSignUp) { // variable that stores page state (signup or login)
          // verify the entered details (fields empty, toast message etc)
          // if everything works, handleSignUp(); 
        }
        else {
          // verify the entered details (fields empty, toast message etc) 
          // if everythign works, handleLogIn(); 
        }

## Step 2: create onClickListener for the sign/login text (already? don't have?) 

    txtSignLogInfo.setOnClickListener(.... {
      public void onClick(View v) {
        if (isSignUp) {
          isSignUp = false; //goes from sign up page to log in page 
          btnSubmit.setTet("LOG IN"); 
          txtSignLogInfo.setText("Don't have an account? Sign up"); 
          edtUsername.setVisibility(View.gone); //no username in login page
        }

        else {
          isSignUp = true;
          btnSubmit.setText("SIGN UP");
          txtSignLogInfo.setText("Already have an account? Log in");
            edtUsername.setVisibility(View.VISIBLE);
          }
        }

## Step 3: create private method for handling signup

    private void handleSignUp(){
      FirebaseAuth.getInstance().createUserWithEmailAndPassword(edtEmail.getText().toString(), edtPassword.getText().toString())
        .addOnCompleteListener(new OnCompleteListener<AuthResult>() {
            @Override
            public void onComplete(@NonNull Task<AuthResult> task) {
              if (task.isSuccessful()) {
                Toast.makeText(MainActivity.this, "Signed up successfully.", Toast.LENGTH_SHORT).show();
                startActivity(new Intent(MainActivity.this, FriendsActivity.class));
              } else {
                  Toast.makeText(MainActivity.this, task.getException().getLocalizedMessage(), Toast.LENGTH_SHORT).show();
              }
            }
        });
    }

    private

## Step 4: create private method for handling login 

    private void handleLogIn() {
      FirebaseAuth.getInstance().signInWithEmailAndPassword(edtEmail.getText().toString(), edtPassword.getText().toString()) 
      .addOnCompleteListener(new OnCompleteListener<AuthResult>() {
        @Override 
         public void onComplete(@NonNull Task<AuthResult> task) {
            if(task.isSuccessful()) {
                Toast.makeText(MainActivity.this, "Logged in successfully.", Toast.LENGTH_SHORT).show();
                startActivity(new Intent(MainActivity.this, FriendsActivity.class));
            } else {
                Toast.makeText(MainActivity.this, task.getException().getLocalizedMessage(), Toast.LENGTH_SHORT).show();
            }
        }
      });
    }




         
        
