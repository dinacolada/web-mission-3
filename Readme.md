# Mission 3

## Part 0, Part 2, Part 2

https://drive.google.com/file/d/12n18185FbEv0_0BjEL1gJ1O-g6O3aoP3/view?usp=sharing


## Part3

- Query 1 - usernames
```sql
SELECT username 
from "Users"
```

- Query 2 - username - number of sent massages
```sql
SELECT u.username, COUNT(m.id) AS number_of_sent_messages
FROM "Users" u
LEFT JOIN "Messages" m ON u.id = m.from
GROUP BY u.username;
```

- Query 3 - username - number of received messages
```sql
SELECT u.username, COUNT(m.id) AS number_of_received_messages
FROM "Users" u
JOIN "Messages" m ON u.id = m.to
GROUP BY u.username
ORDER BY number_of_received_messages DESC
LIMIT 1;
```

- Query 4 - username - average number of sent massages
```sql
SELECT AVG(sent_messages) AS avg_sent_messages
FROM (
    SELECT COUNT(m.id) AS sent_messages
    FROM "Users" u
    LEFT JOIN "Messages" m ON u.id = m.from
    GROUP BY u.id
) AS message_counts;
```

