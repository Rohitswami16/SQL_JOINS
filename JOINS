


Table Structure
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
`dep` table:
| dep_id | dep_name    |
|--------|-------------|
| 1      | Marketing   |
| 2      | Creative    |
| 3      | Development |

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
`employ` table:
| e_name | e_id | dep_id |
|--------|------|--------|
| Neha   | 101  | 1      |
| Isha   | 102  | 2      |
| Bharat | 103  | 1      |
| Pooja  | 104  | NULL   |
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. Equi Join

Query:
------------------------------------------------
select e.e_id, e.e_name, e.dep_id, d.dep_name
from employ e, dep d
where e.dep_id = d.dep_id;
------------------------------------------------

Output:
------------------------------------------------
| e_id | e_name | dep_id | dep_name  |
|------|--------|--------|-----------|
| 101  | Neha   | 1      | Marketing |
| 103  | Bharat | 1      | Marketing |
| 102  | Isha   | 2      | Creative  |
------------------------------------------------
Explanation:*Only records with matching `dep_id` values in both tables are included, so Pooja is excluded due to the `NULL` value in her `dep_id`.


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2. Inner Join

Query:
------------------------------------------------
select e.e_id, e.e_name, e.dep_id, d.dep_name
from employ e inner join dep d
on e.dep_id = d.dep_id;
------------------------------------------------

Output:(Same as Equi Join)
------------------------------------------------
| e_id | e_name | dep_id | dep_name  |
|------|--------|--------|-----------|
| 101  | Neha   | 1      | Marketing |
| 103  | Bharat | 1      | Marketing |
| 102  | Isha   | 2      | Creative  |
------------------------------------------------
*Explanation:* Inner join only includes rows with matching `dep_id` values in both tables, so Pooja is again excluded.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

3. Natural Join
------------------------------------------------

Query:
------------------------------------------------
select * from employ natural join dep;
------------------------------------------------

Output:(Same as Inner and Equi Join)
------------------------------------------------
| e_id | e_name | dep_id | dep_name  |
|------|--------|--------|-----------|
| 101  | Neha   | 1      | Marketing |
| 103  | Bharat | 1      | Marketing |
| 102  | Isha   | 2      | Creative  |
------------------------------------------------
*Explanation:* Natural join automatically joins based on the common column `dep_id`, so Pooja is excluded due to her `NULL` value.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
4. Left Join

Query:
------------------------------------------------
select e.e_name, e.e_id, e.dep_id, d.dep_name
from employ e left join dep d
on e.dep_id = d.dep_id;
------------------------------------------------

Output:
------------------------------------------------
| e_name | e_id | dep_id | dep_name  |
|--------|------|--------|-----------|
| Neha   | 101  | 1      | Marketing |
| Bharat | 103  | 1      | Marketing |
| Isha   | 102  | 2      | Creative  |
| Pooja  | 104  | NULL   | NULL      |
------------------------------------------------
Explanation:* Left join includes all rows from `employ`, so Pooja is included with `NULL` for `dep_name` because there’s no matching `dep_id` in `dep`.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

5. Right Join
------------------------------------------------

Query:
------------------------------------------------
select e.e_id, d.dep_id, d.dep_name
from employ e right join dep d
on e.dep_id = d.dep_id;
------------------------------------------------

Output:
------------------------------------------------
| e_id | dep_id | dep_name    |
|------|--------|-------------|
| 101  | 1      | Marketing   |
| 103  | 1      | Marketing   |
| 102  | 2      | Creative    |
| NULL | 3      | Development |
------------------------------------------------
Explanation: Right join includes all rows from `dep`, so the Development department is included even though no employees are assigned to it. Unmatched `e_id` values are shown as `NULL`.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

6. Right Join with Additional Employee Details

Query:
------------------------------------------------
select e.e_name, e.e_id, e.dep_id, d.dep_id, d.dep_name
from employ e right join dep d 
on e.dep_id = d.dep_id;
------------------------------------------------

Output:
| e_name | e_id | dep_id | dep_id | dep_name    |
|--------|------|--------|--------|-------------|
| Neha   | 101  | 1      | 1      | Marketing   |
| Bharat | 103  | 1      | 1      | Marketing   |
| Isha   | 102  | 2      | 2      | Creative    |
| NULL   | NULL | NULL   | 3      | Development |
------------------------------------------------
Explanation:* The right join still includes the Development department without employees. The repeated `dep_id` column values are due to the join.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

7. Full Outer Join
------------------------------------------------

Query:
------------------------------------------------
select e.e_name, e.e_id, e.dep_id, d.dep_id, d.dep_name
from employ e right join dep d 
on e.dep_id = d.dep_id
union 
select e.e_name, e.e_id, e.dep_id, d.dep_id, d.dep_name
from dep d right join employ e
on e.dep_id = d.dep_id;
------------------------------------------------

Output:
| e_name | e_id | dep_id | dep_id | dep_name    |
|--------|------|--------|--------|-------------|
| Neha   | 101  | 1      | 1      | Marketing   |
| Bharat | 103  | 1      | 1      | Marketing   |
| Isha   | 102  | 2      | 2      | Creative    |
| Pooja  | 104  | NULL   | NULL   | NULL        |
| NULL   | NULL | 3      | 3      | Development |
------------------------------------------------
Explanation: Full outer join combines all rows from both tables. Pooja is included from `employ`, and Development is included from `dep`, with `NULL` in place for non-matching fields.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
8. Self Join

Query:
------------------------------------------------
select e1.e_id
from employ as e1 inner join employ as e2
on e1.dep_id = e2.dep_id and e1.e_id <> e2.e_id;
------------------------------------------------

Output:
| e_id |
|------|
| 101  |
| 103  |
------------------------------------------------
*Explanation:* Self join finds employees within the same department but with different IDs. Both Neha and Bharat are in department 1, so they meet the criteria.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
