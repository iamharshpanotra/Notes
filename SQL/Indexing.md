    1. What is an Index in Databases?
    An index in a database is a performance optimization feature that speeds up the retrieval of rows from a table. It works like an index in a book, helping the database find data faster without scanning every row.
    
    1. How Does an Index Work?
        • When you create an index on a column (or multiple columns), the database builds a sorted structure (like a B-tree or Hash index).
        • This makes it faster to search, filter, and join queries using the indexed column.
    🔹 Without an Index:
    The database must scan every row (full table scan) to find matching data.
    🔹 With an Index:
    The database can quickly locate the required data using the indexed structure.
    
    2. Example of an Index in SQL
    
    CREATE INDEX idx_role_name ON RoleMaster(RoleName);
        • This creates an index named idx_role_name on the RoleName column.
        • Searching for a specific role (WHERE RoleName = 'Customer') will be much faster.
    
    3. Unique Index
    
    [Index(nameof(RoleName), IsUnique = true, Name = "IX_RoleName_Unique")]
public string RoleName { get; set; }
        • This ensures RoleName values are unique.
        • It prevents duplicate roles like "Customer" appearing multiple times.
    
    4. Types of Indexes
    Type	Description
    Primary Index	Automatically created on primary key columns.
    Unique Index	Ensures all values in the column are unique.
    Clustered Index	Sorts and stores rows physically in order. Each table can have only one.
    Non-clustered Index	Creates a separate structure for faster searches (without sorting table rows).
    Composite Index	An index on multiple columns ((FirstName, LastName)).
    
    5. Example Query Performance
    Without Index
    
    SELECT * FROM RoleMaster WHERE RoleName = 'Customer';
        • The database checks every row (slow for large tables).
    With Index
        • The database finds "Customer" directly using the index (much faster!).
    
    6. When to Use an Index?
    ✅ Use an index when:
        • Searching (WHERE, LIKE).
        • Sorting (ORDER BY).
        • Joining tables (JOIN).
        • Enforcing unique constraints.
    ❌ Avoid too many indexes because:
        • They consume storage.
        • They slow down INSERT, UPDATE, and DELETE (since indexes must also be updated).
    
    Conclusion
        • Indexes boost query performance by allowing faster lookups.
        • A unique index prevents duplicate values.
        • They are especially useful for large tables with frequent searches.
    
