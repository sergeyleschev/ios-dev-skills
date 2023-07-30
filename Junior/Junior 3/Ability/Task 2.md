# Task 2

Task: Implement a "favorites" feature for the news app that allows users to save
articles for later viewing. The saved articles should persist across app
launches and the UI should display a list of saved articles. Users should be
able to add and remove articles from the favorites list, and the favorites list
should be accessible from the app's navigation menu.

Solution:

To implement the "favorites" feature, we can create a FavoritesViewController
that will display a list of saved articles. We can use UserDefaults to store the
saved articles as an array of article IDs. When a user saves an article, we can
add its ID to the array and when a user removes an article, we can remove its ID
from the array.

We can create a new button in the article detail view that allows users to add
or remove the article from the favorites list. When the user taps the button, we
can check if the article is already in the favorites list. If it is, we can
remove it, otherwise we can add it.

To display the favorites list, we can add a new cell to the app's navigation
menu that links to the FavoritesViewController. In the FavoritesViewController,
we can retrieve the array of saved article IDs from UserDefaults and use them to
fetch the corresponding article data from the API. We can display the articles
in a table view and allow users to remove articles from the favorites list by
swiping left on the cell.

Differences between Junior 2 and Junior 3:

-   Ability to implement persistence using UserDefaults or a similar mechanism
    to store data across app launches
-   Understanding of UITableView and ability to implement custom table view
    cells
-   Knowledge of view controllers and navigation controllers and ability to
    create a new view controller that can be accessed from the app's navigation
    menu.
