---
title: XX SQL tips
author: Balamurugan
date: '2020-12-29'
slug: xx-sql-tips
categories: []
tags: []
description: Desc
hacker_news_id: ''
lobsters_id: ''
meta_img: /images/image.jpg
---

1.Count uniques ones using count(Distinct col_name)
2.Count number of students in a class use group by. Count number, to count number of students in a class against each student use count(*) over (Partition by team_id) as team_size
https://stackoverflow.com/questions/60622404/how-to-solve-leetcode-sql-find-the-team-size-using-partition-by
3.Want to rank instead of count, use dense_rank() over (partition by user_name)
4.Count(*) and Count(1) are just the same except for coun(1) doesnt include nulls. However, in Postgres count(*) is 10% faster
5.The sold-products names for each date should be sorted lexicographically. 
6.Want to add all names in group by? GROUP_CONCAT(distinct STUDENT ORDER BY STUDENT ASC SEPARATOR ',')
7.Truncate command deletes all row in one go wihtout a need for where clause unlike delete command
8.Length() function finds the length of String
9.Group by month and year using LEFT ex:left(date,7)
10.Do you know you can input an sql table as input in where clause in the below format
WHERE  ( customer_id, order_date ) IN (SELECT customer_id, 
                                              Min(order_date) 
                                       FROM   delivery 
                                       GROUP  BY customer_id) 
11. Do you write too many like to match strings? time to move to REGEXP https://www.geeksforgeeks.org/mysql-regular-expressions-regexp/

12. Self join is a good way to cross tab the data, find how neighbouring enteies are doing
and capture any missing ones due to nul
13. Always do the join with fewer rows and columns possible
14. case and If statements can be used interchangabealy n some cases but case is faster
15. Group by statements need a column to group by and aggregation function applied on a column. However only one can exist in a group by without need for other. For exmaple in a group by you can pick only the name of customer with maximum order or maximum number of oders
16. REGEXP for email verification:SET @pattern = '^([a-zA-Z0-9_\-]+\.)*[a-zA-Z0-9_\-]+@([a-zA-Z0-9_\-]+\.)+(com|org|edu|net|ca|au|coop|de|ee|es|fm|fr|gr|ie|in|it|jp|me|nl|nu|ru|uk|us|za)$'
17. COnditions can be included in Aggregate functions eg: SUM(rating < 3)
18. Always keep an eye on should you report the list of zeros?






https://medium.com/better-programming/numpy-illustrated-the-visual-guide-to-numpy-3b1d4976de1d



https://github.com/kamyu104/LeetCode-Solutions/blob/master/MySQL/consecutive-available-seats.sql



