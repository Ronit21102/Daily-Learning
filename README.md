# Daily-Learning
8 Nov 2024 i will be updating daily whatever i lernt 
ACID and SQL

9th Nov
Architecture
![image](https://github.com/user-attachments/assets/d3642a2d-b6a6-4479-958e-717fb97fab44)
Caching
![image](https://github.com/user-attachments/assets/f9f57f1e-cdfe-4453-99df-ca619f8f0a74)
CDN
![image](https://github.com/user-attachments/assets/365d4762-2cea-4bb8-bf34-f533ab3ea4be)

More Optimised Architecture
![image](https://github.com/user-attachments/assets/b3ed74ad-808a-4804-95e5-7704b44f5424)

13th nov
How Caching Works in Redux Toolkit Query with Tags
Tag Types (tagTypes):

Think of tagTypes as a way to categorize or label specific parts of your data in the cache.
In your example, tagTypes: ["DashboardMetrics"] tells Redux that you have a category of data called DashboardMetrics. This type is like a label that will help Redux know which part of the cache relates to the dashboard metrics.
Provides Tags (providesTags):

When you use providesTags in a query (like getDashboardMetrics), you're tagging the result of this endpoint with a specific label. Here, the result of the getDashboardMetrics query is tagged with DashboardMetrics.
What this does is allow Redux to remember the data fetched by this query under the tag DashboardMetrics.
Any component or function that uses this query endpoint will now rely on the cached result for DashboardMetrics if it exists, which saves the need for repetitive network requests.
Invalidates Tags (invalidatesTags):

When you perform a mutation (e.g., adding, updating, or deleting data), you often want to invalidate or refresh certain cached data so that it’s up-to-date.
For example, if you had an endpoint updateDashboardMetrics that updates the dashboard metrics, you could set invalidatesTags: ["DashboardMetrics"] on this endpoint.
This would tell Redux Toolkit Query to invalidate any cached data associated with DashboardMetrics, triggering a re-fetch of getDashboardMetrics so that the cache stays fresh.
Example Scenario of How This Works
Imagine this flow:

Initial Fetch:

When useGetDashboardMetricsQuery is called for the first time, it fetches data from the /dashboard endpoint, and caches it under the DashboardMetrics tag.
This cached result will be used by any other component that calls useGetDashboardMetricsQuery as long as it hasn’t been invalidated.
Updating Data:

Suppose you have a different mutation endpoint, like updateDashboardMetrics, where you edit dashboard metrics.
By setting invalidatesTags: ["DashboardMetrics"] on this mutation, every time updateDashboardMetrics is called, Redux Toolkit Query knows to invalidate the cache for any data tagged as DashboardMetrics.
Automatic Re-fetch:

When DashboardMetrics is invalidated, Redux Toolkit Query automatically re-fetches the data for useGetDashboardMetricsQuery to ensure your UI has the most current data. This way, your components don’t have to handle cache invalidation or re-fetching manually—it’s all handled based on these tags.
Key Benefit: Efficient and Up-to-Date Data
Using providesTags and invalidatesTags automates cache management. You don’t need to worry about when to fetch or update the data—the tags handle that for you. This is especially useful in apps with complex, interconnected data that need to stay in sync across multiple components.

