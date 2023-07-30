# Task 4

Task: Implement a feature to allow users to search for messages in a chat
conversation. The search should be performed in real-time and should highlight
the matching text within each message. The search feature should also provide
suggestions for related search terms.

Solution:

To implement this feature, we can add a search bar to the chat conversation
screen. As the user types in the search bar, we can use the **`filter`** method
on the array of messages to filter out any messages that do not match the search
query. We can then display the filtered messages in a table view.

To highlight the matching text within each message, we can use the
**`NSAttributedString`** class to set the
**`NSAttributedString.Key.backgroundColor`** property of the matching text to a
different color.

To provide suggestions for related search terms, we can use a third-party
library such as **`AlgoliaSearch`** or **`Elasticsearch`** to perform a
full-text search on the chat messages and display the results as suggested
search terms.
