# Android Model-View-Presenter Tutorial

## The Contract
The first thing I will typically do whenever constructing an activity into a MVP architecture, I will write the contract the view and the presenter use to communicate with one another. The base structure will look something like this: 

```
public interface ActionItemDetailContract {

    interface View {
    	//this is where all your methods where you would want to manipulate the view
    	//such as turn on a loading spinner, populate data into the recyclerview    
    }

    interface Presenter {
        //this is where all your methods for clickevents should go
   		 //essentially anything the user can interact with you delegate to the presenter here
    }

}
```

To make contracts a little simpler, there are two interfaces called `BaseView` and `BasePresenter` which look like: 

```
//this is only needed for fragments
public interface BaseView<T> {

    void setPresenter(T presenter);

}

//this can be used for everything and is called in the OnResume()
public interface BasePresenter {

    void start();

}
```
The reason why the `BaseView` is only needed for fragment contracts is something that will be explained a little later. 

## Implementing in an Activity
So for now lets create a contract for the `ActionItemDetailActivity`:

```
public interface ActionItemDetailContract {
    
    interface View {
        //present the response data onto the UI
        void showActionItem(Response response);
        
        //present the edit priority dialog to the user
        void showPriorityDialog();
        
        //grab all editable fields from the ui
        Response getActionItemDetails();
    }

    interface Presenter extends BasePresenter {
        
        //respond to back button press or arrow in the action bar
        void backButtonClicked();
        
        //user clicked edit priority button
        void editPriorityButtonClicked();
        
        //user clicked the save button
        void saveButtonClicked();
    }

}
```

So now that the contract is setup, its time to go implement these interfaces in the view and the presenter. 


## The Presenter

First let's implement the Presenter contract, create a new class `ActionItemDetailPresenter` and then implement the contract. Go ahead and implement all the methods from the contract by using the shortcut `ctrl + i` or `cmd +i`, select all the methods and click ok.

Then generate a constructor where we will be passing in the View portion of the contract. This is what will be used throughout the presenter class to call actions upon the view.

So for now the presenter should look something like this.  

```
public class ActionItemDetailPresenter implements ActionItemDetailContract.Presenter {

    private ActionItemDetailContract.View view;

    public ActionItemDetailPresenter(ActionItemDetailContract.View view) {
        this.view = view;
    }

    @Override
    public void start() {
       //example of how to communcate with the view
		view.showData(new Response());
    }

    @Override
    public void backButtonClicked() {

    }

    @Override
    public void editPriorityButtonClicked() {

    }

    @Override
    public void saveButtonClicked() {

    }
}
```

## The View
Now open up the activity and implement the interface using the shortcut from the previous step and implement all View methods. So it should look something like this: 

```
public class ActionItemDetailActivity extends AppCompatActivity
        implements ActionItemDetailContract.View {
     ...
        
	 @Override
    public void showActionItem(Response response) {

    }

    @Override
    public void showPriorityDialog() {

    }

    @Override
    public Response getActionItemDetails() {
        return null;
    }       	
       
}

```

Then we need to instantiate the presenter. Create a field, instantiate in `OnCreate()` and then call `presenter.start()` in the `onResume()`. 

```
	private ActionItemDetailPresenter presenter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
    	...
        presenter = new ActionItemDetailPresenter(this); 
        ...
    }
    
    @Override
    protected void onResume() {
        super.onResume();
        presenter.start();
    }
```

So now there is ever a user action, you can communicate with the presenter by calling `presenter.onButtonClick()` or whatever you called the method in your contract.


## Wire up an action and present the change

So now that the base foundation of the view and presenter are set up, let's go ahead and respond to a user action and have the presenter respond by calling a function on the UI. 

In the activity, setup a click listener on the edit priority button, and we will notifiy the presenter whenever the button is clicked. 

```
editPriorityBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                presenter.editPriorityButtonClicked();
            }
        });
```
Then in the presenter, call upon the view to do present the edit priority dialog box.

```
	@Override
    public void editPriorityButtonClicked() {
        view.showPriorityDialog();
    }
```

Finally back in the activity, add the logic to show the edit priority dialog fragment

```
    @Override
    public void showPriorityDialog() {
        DialogFragment editPriorityDialog = new EditPriorityDialogFragment();
        editPriorityDialog.show(getSupportFragmentManager(), "EditPriorityDialogFragment");
    }
```

That's it! Now your view and presenter can communicate with one another. The goal with this approach is essentially to make the activity/view as dumb as possible by delegating all actionable events to the presenter. Then the presenter can be used to determine what to present onto the view. 


# What about Fragments?

This is where things get a little bit trickier because fragments have a messier lifecycle than compared to that of Activities. So this is where extending `BaseView` in the View portion of the contract will help tie the fragments presenter lifecycle to the Activity. The `Presenter` inside `BaseView<Presenter>` is simply referencing the `Presenter` interface within this contract. 

```
public interface ActionItemContract {

    interface View extends BaseView<Presenter> {
        
    }

    interface Presenter extends BasePresenter {
        
    }
}
``` 
The purpose of doing it this way is to instantiate the presenter for the fragment inside of the activity passing along the reference to the fragments view. So the activity should look something like this: 

```
new SurveyLandingPresenter(SurveyLandingFragment.newInstance());
```

Then going into the presenter, we will hook up the reference to the view and then call setPresenter in the constructor so that the view will have a reference to communicate with this presenter. 

```
public class ActionItemPresenter implements ActionItemContract.Presenter {

    private final ActionItemContract.View view;

    public ActionItemPresenter(ActionItemContract.View actionItemView) {
        this.view = actionItemView;
        actionItemView.setPresenter(this);
    }
}
```

Finally in the fragment, implement the `setPresenter()` method for the view to communicate with the presenter. 

```
    @Override
    public void setPresenter(ActionItemContract.Presenter presenter) {
        this.presenter = presenter;
    }
```