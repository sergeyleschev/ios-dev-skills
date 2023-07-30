# Task 5

Task: Build a news app that displays a list of articles from a JSON API, with
the ability to search for articles and save them as favorites. The app should
have the following features:

1. The app should fetch articles from a JSON API and display them in a table
   view.
2. Each cell in the table view should display the article's title, description,
   author, and published date.
3. The app should have a search bar that allows users to search for articles by
   keyword.
4. When the user taps on an article in the table view, they should be taken to a
   detail view that displays the article's content and image.
5. The app should allow users to save articles as favorites, which should be
   persisted across app launches.

Requirements:

-   Use Swift, UIKit, and Foundation frameworks.
-   Use URLSession to fetch data from the JSON API.
-   Use Codable to decode the JSON data into Swift objects.
-   Use Core Data to persist favorite articles.
-   Use MVVM design pattern to organize code.

Solutions:

-   First, create a model for the articles that conforms to Codable.
-   Next, create a service class that uses URLSession to fetch articles from the
    JSON API and decode them into Swift objects.
-   Create a view model class that manages the data for the table view and
    detail view.
-   Implement the table view using a UITableViewController and the cell
    prototype to display the articles.
-   Implement the search bar using the UISearchBarDelegate to filter the
    articles.
-   Implement the detail view using a UIViewController and the storyboard to
    display the article's content and image.
-   Use Core Data to persist favorite articles by creating a FavoriteArticle
    entity and a FavoriteArticleViewModel class to manage the favorite articles.
-   Implement the favorite button in the detail view to add or remove the
    article from the favorite list.
-   Use MVVM to organize the code by separating the data management logic from
    the view controllers.

Differences from Junior 2 level:

-   The Junior 3 developer should be able to work with Core Data and persist
    data.
-   The Junior 3 developer should be able to implement more complex user
    interfaces, such as search bars and detail views.
-   The Junior 3 developer should have a good understanding of MVVM design
    pattern and be able to organize code effectively.
-   The Junior 3 developer should be able to implement more complex features,
    such as saving articles as favorites and persisting them across app
    launches.
