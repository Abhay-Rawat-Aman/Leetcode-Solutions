# 3570. Find Books with No Available Copies

**Difficulty:** Easy  
**Topics:** Database   
**LeetCode:** https://leetcode.com/problems/find-books-with-no-available-copies/description/

---

## Solution - Database

---

### MySQL Code

```MySQL
# Write your MySQL query statement below
select book_id,title, author,genre,publication_year, total_copies as  current_borrowers from library_books l
where total_copies = 
(select count(*) from borrowing_records b where b.book_id=l.book_id and return_date is null )
order by total_copies desc,title;
```

