# Task 1

Task:

Create a basic UI in Interface Builder (xib) for an app that displays a list of
movies. The UI should consist of a table view that displays a list of movie
titles and their release dates. The list should be scrollable and should display
at least 5 movie titles.

Solution:

Step 1: Create a new xib file by selecting File -> New -> File -> User Interface
-> View.

Step 2: Drag and drop a Table View object onto the View.

Step 3: Adjust the size of the Table View object to fit the screen.

Step 4: Set the Table View's prototype cell to "Basic" by selecting the Table
View object and going to the Attributes Inspector.

Step 5: Add a Label to the prototype cell and adjust its position and size as
desired.

Step 6: Set the prototype cell's Identifier to "MovieCell" in the Attributes
Inspector.

Step 7: Create a new subclass of UITableViewCell called "MovieTableViewCell".

Step 8: Open the xib file and set the Table View's Cell class to
"MovieTableViewCell".

Step 9: Implement the MovieTableViewCell class by adding a UILabel property for
the movie title and a UILabel property for the release date. Also, create a
method to set the values of these properties.

Step 10: Implement the UITableViewDataSource protocol in the View Controller
that will display the list of movies.

Step 11: In the View Controller's viewDidLoad method, register the
MovieTableViewCell class for the "MovieCell" identifier.

Step 12: Implement the UITableViewDataSource method numberOfRowsInSection to
return the number of movies to be displayed.

Step 13: Implement the UITableViewDataSource method cellForRowAt to dequeue a
reusable MovieTableViewCell object and set its properties using the movie data.

Step 14: Run the app to test the UI and ensure that the list of movies is
displayed correctly in the Table View.
