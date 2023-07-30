# Task 5

Task:

You are given a simple app that fetches a list of users from an API and displays
them in a table view. Your task is to implement pagination for the table view.
The API supports pagination by accepting a "page" parameter that returns a
specific set of users.

Requirements:

-   The table view should initially display the first set of users.
-   When the user scrolls to the bottom of the table view, the app should fetch
    the next set of users and append them to the table view.
-   Each page should display 20 users.
-   When there are no more users to fetch, the table view should display a "No
    more users" message at the bottom.

Technical requirements:

-   Use Swift, Foundation, and UIKit.
-   Use the MVVM architecture pattern.

Solution:

To implement pagination for the table view, we can follow these steps:

1. Define a property called **`currentPage`** in the view model to keep track of
   the current page number.
2. In the **`fetchUsers`** method, append the current page number to the API
   endpoint and fetch the users.
3. When the users are fetched successfully, append them to the **`users`** array
   in the view model.
4. In the view controller, implement the
   **`tableView(_:willDisplay:forRowAt:)`** method to detect when the user
   scrolls to the bottom of the table view.
5. In the **`tableView(_:willDisplay:forRowAt:)`** method, check if the current
   row index is equal to the last index of the **`users`** array. If so,
   increment the **`currentPage`** property and call the **`fetchUsers`** method
   again.
6. In the **`fetchUsers`** method, check if the number of fetched users is less
   than 20. If so, set the **`isFetchingMore`** property in the view model to
   **`false`**.
7. In the **`tableView(_:numberOfRowsInSection:)`** method, check if the
   **`isFetchingMore`** property is **`true`**. If so, return the number of rows
   in the **`users`** array plus 1. Otherwise, return the number of rows in the
   **`users`** array.
8. In the **`tableView(_:cellForRowAt:)`** method, check if the current row
   index is equal to the last index of the **`users`** array and the
   **`isFetchingMore`** property is **`true`**. If so, display a loading
   indicator cell.
9. In the **`fetchUsers`** method, check if the number of fetched users is less
   than 20 and the **`currentPage`** property is greater than 1. If so, set the
   **`noMoreUsers`** property in the view model to **`true`**.
10. In the **`tableView(_:numberOfRowsInSection:)`** method, check if the
    **`noMoreUsers`** property is **`true`**. If so, return the number of rows
    in the **`users`** array plus 1 for the "No more users" message cell.

Differences from Middle 2:

-   This task requires implementing pagination for a table view using the MVVM
    architecture pattern. This requires a solid understanding of how to separate
    concerns between the view, view model, and model layers of an app.
-   The implementation of pagination requires more complexity than the previous
    tasks, such as keeping track of the current page number, detecting when the
    user scrolls to the bottom of the table view, and displaying a "No more
    users" message when there are no more users to fetch.
-   The solution requires handling asynchronous network requests and displaying
    a loading indicator cell while fetching more users.
-   The solution requires handling edge cases such as fetching less than 20
    users, setting a flag to indicate when there are no more users to fetch, and
    displaying a message cell when there are no more users to fetch.
