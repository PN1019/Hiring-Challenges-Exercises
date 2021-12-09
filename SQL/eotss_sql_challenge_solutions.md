
- Query 1 - total pageviews in last 7 days

```sql:
select sum(pageviews)
from ga_session_views
where hit_timestamp > DATE_SUB(CURRENT_TIMESTAMP, INTERVAL 7 day);
```
- Query 2 -all sessions with organic medium

```sql:
select count(session_id)
from ga_session_features
where medium = 'organic';
```
- Query 3 - nodes and their pageviews with organic medium in the last 30 days

```sql:
select node_id, sum(pageviews)
from ga_session_views views
inner join ga_session_features features
  on features.session_id = views.session_id
where medium = 'organic' and hit_timestamp > DATE_SUB(CURRENT_TIMESTAMP, INTERVAL 30 day)
group by node_id
order by pageviews desc;
```
- Query 4- This query calculates each session's duration in minutes and then averages the duration by category
```sql:
select device_category, avg(t1.sessionLen) as avgSessionLength
from ga_session_features features
inner join
  (
  -- calculate the duration of each session
  select session_id, timestampdiff(minute, min(hit_timestamp), max(hit_timestamp)) as sessionLen
  from ga_session_views
  group by session_id
  ) t1
    on features.session_id = t1.session_id
group by device_category;
```
