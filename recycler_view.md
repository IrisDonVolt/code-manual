# How to create Adapter for RecyclerView

# Table of contents:
1. [Step 1: create the Adapter class](#step-1-create-the-adapter-class)
2. [Step 2: create the holder class](#step-2-create-the-myholder-class-so-that-we-can-use-its-object-the-holders-inside-the-recycler-viewclass-should-be-created-inside-adapter)
3. [Step 3: defining methods](#step-3-define-the-methods-indicated-above-holder-class)
4. [Step 4: defining the interface](#step-4-define-the-interface-used-to-handle-holder-activity) 
5. [Step 5: setting interface in click listener](#step-5ish-use-the-interface-in-a-click-listener)
6. [Step 6: using/overriding the interface](#step-6-using-the-interface-to-handle-holder-activity) 



## Step 1: create the Adapter class 

    public class MyAdapter extends Recyclerview.Adapter<MyAdapter.MyHolder> {
        ArrayList<Object> data; // this is an arrayList that holds the objects containing the values (e.g. Animal class with getters and setters) 
        Context context; 
        MyInterface myInterface; // interface to deal with holder actions (like clicking; this will be overwritten in MainActivity)

        /* constructor for adapter */
        public MyAdapter(ArrayList<Object> data, Context context, MyInterface myInterface) {
            this.data = data;
            this.context = context; 
            this.myInterface = myInterface; 
        }
    }

## Step 2: create the MyHolder class so that we can use its object (the holders inside the recycler view)(class should be created inside Adapter) 

    class MyHolder extends RecyclerView.ViewHolder {
        //Declare views to be displayed (TextView, ImageView etc.)
        /*constructor* 
        public MyHolder(@NonNull View itemView) {
            super(itemView); 
            //initialize the variables by using itemView.findViewById()

## Step 5(ish): use the interface in a click-listener 
            itemView.setOnClickListeniner(new View.onClickListener() {
                @Override 
                public void onClick(View view) {
                    myInterface.onItemClick(getAdapterPosition()); //calling the interface for clicking functions and passing position of whatever was clicked
                }
            });
        }
    }

## Step 3: define the methods indicated (above holder class) 

    public MyHolder onCreateViewHolder(.....) {
        // inflate the holder thing on the recycler view 
        View view = LayoutInflater.from(context).inflate(R.layout.holderlayout, parent, false); 
        return new MyHolder(view); 
    }

    public void onBindViewHolder(....) { 
        holder.variableName.setText/ImageResource/SomethingElse(data.get(position).getSomething()); 
    }

    public int getItemCount() {
        return data.size(); 
    }

## Step 4: define the interface used to handle holder activity 
    interface MyInterface {
        void onItemClick(int position); 
    }

[Step 5](#step-5ish-use-the-interface-in-a-click-listener)

## Step 6: Using the interface to handle holder activity
    // go to MainActivity
    @Override 
    public void onItemClick(int position) {
        // whatever has to be done when item is clicked
        // for example: Toast messages, starting a new activity, etc.
    }


