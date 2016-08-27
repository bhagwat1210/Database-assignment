# Database-assignment

— find the 5th higher marks score 

select name from 
(select name, rank() over(order by Marks desc) "rank1" from students ) where "rank1"=5;

— find the 5th higher marks using correlated subquery 

select name from students s where 5=(select count(distinct(name)) from students st where st.marks>=s.marks);

— getting the individual rank within the challenges 

select challenge_id,hacker_id,rank() over(partition by challenge_id order by score desc) "Rank" from submissions;
