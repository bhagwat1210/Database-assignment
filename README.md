# Database-assignment

— find the 5th higher marks score 

select name from 
(select name, rank() over(order by Marks desc) "rank1" from students ) where "rank1"=5;

— find the 5th higher marks using correlated subquery 

select name from students s where 5=(select count(distinct(name)) from students st where st.marks>=s.marks);

— getting the individual rank within the challenges 

select challenge_id,hacker_id,rank() over(partition by challenge_id order by score desc) "Rank" from submissions;

-- Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.Write a query to output all such symmetric pairs in ascending order by the value of X.

SELECT p1.rowid,p2.rowid,p1.*,p2.* FROM FUNCTIONS P1, FUNCTIONS P2 WHERE P1.X = P2.Y AND P1.Y = P2.X  AND P1.ROWID <> P2.ROWID;
