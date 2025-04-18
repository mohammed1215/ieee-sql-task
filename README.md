# ieee-sql-task
1- i didn't know how to solve this one
```sql
```

2- 
``` sql
select product_id, product_name, description
from products
where description like '%SN____-____ %'
 or description like '%SN____-____' 
 or description like 'SN____-____%';
 ```

3- in this problem my code didn't work fully
```sql
with 

 latest_score as
(
    select student_id,
            subject,
            if(score-lag(score) over( order by student_id,subject,exam_date) > 0 and subject = lag(subject) over(order by student_id,subject,exam_date),lag(score) over( order by student_id,subject,exam_date),null)  as first_score,
        score as latest_score

     from scores where (student_id,subject) in (select student_id,subject from scores group by subject ,student_id having count(student_id)>1 ))
select * from latest_score
where latest_score.first_score is not null;
```

4-
```sql
select contest_id,round(count(*) * 100/(select count(user_id) from Users),2) as percentage  from Users u join Register r on u.user_id = r.user_id 
group by contest_id
order by percentage desc,contest_id
```
