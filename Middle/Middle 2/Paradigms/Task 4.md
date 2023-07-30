# Task 4

Task: Create a simple weather app that displays the current temperature and
weather condition for a given location. The app should allow the user to search
for a location by name, and use a weather API to retrieve and display the
weather information. The app should also allow the user to save their favorite
locations and view the weather information for those locations without needing
to search again. The user should be able to remove a saved location from their
list of favorites.

Solution:

Here's one possible solution:

1. Create a new Xcode project using the "Single View App" template.
2. Add a search bar and a table view to the main view controller.
3. Create a custom cell for the table view that displays the location name,
   current temperature, and weather condition.
4. Implement the search bar delegate methods to search for locations using the
   OpenWeatherMap API (or any other weather API of your choice).
5. When the user taps a search result, display the weather information for that
   location in the custom cell.
6. Add a button to the custom cell that allows the user to save that location to
   a list of favorites.
7. Add a new view controller for the list of favorites, and implement the table
   view data source and delegate methods to display the saved locations.
8. Implement a way to remove a saved location from the list of favorites, such
   as a swipe-to-delete gesture or an edit button.
9. Implement persistence for the list of favorite locations, such as using Core
   Data or User Defaults.

Differences from Middle 1:

-   Uses a weather API to retrieve weather information, requiring knowledge of
    network requests and parsing JSON data.
-   Implements persistence for the list of favorite locations, requiring
    knowledge of data storage and retrieval.
-   Adds a feature to save and remove locations from a list of favorites,
    requiring knowledge of table view data manipulation and possibly other UI
    elements.
