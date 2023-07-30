# Task 3

Task: Create (explain) a news app that displays a list of articles from a JSON
API and allows the user to select an article to view the full details.
Additionally, implement a search feature that allows the user to search for
articles based on keywords.

Requirements:

-   Use URLSession to retrieve the data from the API.
-   Parse the JSON response using Codable.
-   Display the list of articles in a table view or collection view.
-   When the user selects an article, display the full details in a new view
    controller.
-   Implement a search bar that allows the user to search for articles based on
    keywords.
-   Filter the list of articles based on the user's search query.
-   Allow the user to cancel the search and return to the full list of articles.
-   Handle any errors that may occur during network requests or parsing.

Solution: Here's an example implementation of the news app:

-   First, create a new Xcode project and add a view controller for the article
    list and another view controller for the article details.
-   Create a new Swift file for the Article model, which conforms to Codable and
    represents a single article.
-   Use URLSession to retrieve the data from the API and parse the JSON response
    using Codable. This can be done in a separate file or in the view controller
    itself.
-   Display the list of articles in a table view or collection view in the
    article list view controller.
-   When the user selects an article, pass the selected article to the article
    details view controller and display the full details in that view
    controller.
-   Implement a search bar in the article list view controller and allow the
    user to search for articles based on keywords.
-   Filter the list of articles based on the user's search query and update the
    table view or collection view to display only the filtered articles.
-   Allow the user to cancel the search and return to the full list of articles
    by clearing the search bar and reloading the table view or collection view.
-   Handle any errors that may occur during network requests or parsing by
    displaying an error message to the user.

Some differences between this task and the Junior 1 level tasks include the use
of URLSession to retrieve data from an API, parsing the JSON response using
Codable, and implementing a search feature. These skills require a deeper
understanding of networking and data handling in iOS development, as well as
more advanced UI design and implementation.
