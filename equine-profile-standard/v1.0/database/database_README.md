# Database Schema Files

**Equine Profile Standard v1.0**  
Horse AI — TechXZone Pvt Ltd | horseai.org

---

## ⚠️ Important — Read Before Running

All SQL files in this folder contain `DROP TABLE` statements at the beginning.

**Running any of these files will permanently delete any existing tables with the same names from your database before creating new ones.**

The tables affected are:

- `owners`
- `pedigree`
- `horses`
- `stables`

If these table names already exist in your database, **all data in them will be lost and cannot be recovered.**

---

## Before You Run

- Back up your existing database
- Confirm that the table names above do not conflict with your existing tables
- Run in a test environment first before applying to a production database

---

## Files in This Folder

| File | Database |
|------|----------|
| `equine_profile_standard_mysql_v1.0.sql` | MySQL |
| `equine_profile_standard_postgresql_v1.0.sql` | PostgreSQL |
| `equine_profile_standard_sqlite_v1.0.sql` | SQLite |
| `equine_profile_standard_mongodb_v1.0.js` | MongoDB |

---

## Why DROP TABLE Is Included

The `DROP TABLE IF EXISTS` statements are included to allow safe re-runs of the schema — for example during development or when upgrading to a newer version of the standard. They ensure the script runs cleanly from scratch each time without manual cleanup.

If you do not want existing tables dropped, remove the `DROP TABLE IF EXISTS` lines before running.

---

*Equine Profile Standard v1.0 | MIT Licensed | Horse AI — TechXZone Pvt Ltd*
