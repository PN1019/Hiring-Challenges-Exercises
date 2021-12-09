## Solution
This question is pretty straightforward. We have 2 tables, 1 that has all the users' streaming sessions and another that has all the content created. 
All we need to do is join the two tables by the stream_id and the date and pull data in terms of creator_id and total_mins_viewed.

```sql:
SELECT
    creator_id,
    SUM(mins_viewed) AS total_mins
FROM creatorStreams AS C
JOIN viewWatches AS V
ON C.stream_id = V.stream_id
    AND C.date = V.date
GROUP BY
    creator_id
ORDER BY 2 DESC
``` 
