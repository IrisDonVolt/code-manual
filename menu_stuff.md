# Creating and handling menu view

## Step 1: Create a new resource directory 
* Right-click on `res` and create new menu resource directory.
* Add items using `<item>` tag
  
    ```
    <!-- file name = my_menu-->
    <item
      android:id="@+id/menu_item1"
      android:icon="@drawable/ic_icon"
      app:showAsAction="always"
      android:title="MyMenuItem" />
    ```

## Step 2: Inflating the menu in the required activity
* Go to the Activity that will contain the menu

    ```
      // after onCreate method
      @Override
      public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.my_menu, menu);
        return true;
      }
    ```

## Step 3: Handling clicks 

    @Override 
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
      if (item.getId() == R.id.menu_item1) {
        // do the required tasks
        // example start a new activity 
      }
      return true; 
    }
