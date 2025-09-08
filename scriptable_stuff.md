# Working with Scriptable library 
Scriptable is used (as far as I know) to evaluate arithmetic expressions. 

## Step 1: Import the Scriptable library 

    import org.mozilla.javascript.Context; 
    import org.mozilla.javascript.Scriptable; 

## Step 2: Write the main code wherever you want to evaluate the expression

    try {
        Context context = Context.enter(); 
        context.setOptimizationLevel(-1); 
        Scriptable scriptable = context.initStandardObjects(); 

        // create the expression to be evaluated (String type)
        String result = context.evaluateString(scriptable, display_string, "Javascript", 1, null).toString();
    }
    catch (Exception e) {
        // Toast message: Error in computing result 
    }
