# Task 3

Task: Implement a caching mechanism for news articles in the news app. The app
should store previously loaded articles in a cache and retrieve them from the
cache if they're requested again. The cache should be able to store at least 50
articles, and it should automatically remove the least recently used articles if
the cache reaches its maximum capacity.

Solution:

To implement the caching mechanism, you can use the NSCache class provided by
Foundation. Here's how you can do it:

1. Create a new class named "NewsArticleCache" that extends NSCache and conforms
   to the NSCacheDelegate protocol.
2. In the init method of the NewsArticleCache class, set the delegate property
   to self and set the totalCostLimit property to 50 (the maximum number of
   articles the cache should store).
3. Implement the optional method "cache(\_:willEvict:)" of the NSCacheDelegate
   protocol. This method is called by the cache just before an item is removed
   from the cache. In this method, you can perform any necessary cleanup before
   the item is removed from the cache.
4. In your NewsArticleAPI class (which is responsible for fetching news articles
   from the API), modify the fetchArticles method to check if the requested
   article is already in the cache. If it is, return the article from the cache.
   If it's not in the cache, fetch it from the API and add it to the cache.
5. In the fetchArticles method, before adding the article to the cache,
   calculate its size in bytes using the Data object and set the cost property
   of the cache item to this value. This ensures that the cache stays under its
   maximum size limit.
6. When the cache reaches its maximum size limit, the NSCache class
   automatically removes the least recently used item from the cache. This
   behavior is built into the class and doesn't require any additional code from
   you.

Differences from Junior 2:

This task requires the developer to have a deeper understanding of caching
mechanisms and memory management. It also requires the use of the NSCache class,
which is a more advanced topic than the URLSession and JSON serialization used
in the Junior 2 tasks. Finally, this task requires the developer to consider
performance and efficiency, as the caching mechanism should be able to handle a
large number of articles without consuming too much memory.
