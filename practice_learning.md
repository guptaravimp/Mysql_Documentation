# On delet cascade? 
Suppose you have a Worker with Worker_id = 1, and there are corresponding bonus records in the Bonus table that reference worker_ref_id = 1.

If that worker with Worker_id = 1 is deleted from the Worker table, all bonus records in the Bonus table that have worker_ref_id = 1 will also be automatically deleted.
```
CREATE TABLE Bonus (
    worker_ref_id INT,
    bonus_amount INT,
    bonus_date DATETIME,
    FOREIGN KEY (worker_ref_id)
      REFERENCES Worker(worker_id)
      ON DELETE CASCADE
);

```
