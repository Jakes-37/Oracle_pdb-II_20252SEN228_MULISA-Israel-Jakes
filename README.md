# Assignment II: Oracle Pluggable Database Management Report

Pluggable Database (PDB): a portable, self-contained logical database that functions as a regular standalone database to applications but operates under a shared Container Database (CDB).

TASK 4,

**Date:** September 22, 2026  
**Course:** Advanced Database Systems / PL-SQL  
**Environment:** Oracle Database 21c Express Edition (XE) via Docker on Kali Linux

---

## 1. Overview of Tasks
This assignment demonstrates the administrative lifecycle of a Pluggable Database (PDB) operating within a Container Database (CDB) cluster environment. The exercise encompasses structural container creation, operational lifecycle modification, administrative role handling, structural deletion, and environment verification.

---

## 2. Oracle Environment Configuration
*   **Operating System Host:** Kali Linux (Rolling Release)
*   **Database Management Clients:** Oracle SQL Developer Extension for Visual Studio Code 
*   **Administrative Access Role:** `SYSDBA`

---

## 3. Core Task Execution Logs

### Task A: Pluggable Database Creation
The target pluggable container database was successfully provisioned using isolated directory definitions mapped directly within the runtime environment engine.

```sql
CREATE PLUGGABLE DATABASE ja_db_20252SEN228
ADMIN USER jakes_plsqlauca_20252SEN241 IDENTIFIED BY "israel290" 
FILE_NAME_CONVERT=('pdbseed','jakes_db_20252SEN228');

ALTER PLUGGABLE DATABASE ja_db_20252SEN228 OPEN;
ALTER PLUGGABLE DATABASE ja_db_20252SEN228 SAVE STATE; (For saving the user even when the docker restarts).
```

### Task B: Environment Status Verification
To establish factual evidence of active operation, the following dictionary lookup was executed to confirm a `READ WRITE` operational profile:

```sql
SELECT name, open_mode FROM v$pdbs WHERE name = 'JAKES_DB_20252SEN228';
```
*Verification State: Active / Online*

### Task C: Pluggable Database Deletion
The database infrastructure was intentionally torn down and wiped cleanly from the container runtime system using structural dropping protocols:

```sql
ALTER PLUGGABLE DATABASE ja_db_20252SEN228 CLOSE IMMEDIATE;
DROP PLUGGABLE DATABASE ja_db_20252SEN228 INCLUDING DATAFILES;
```

---

## 4. Challenges Faced & Solutions

### First Challenge was OEM dashboard screenshot included, i didnt access it
---

## 5. Integrity Statement

I declare on my honor that the database configurations, query outputs, and log documentation shown in this submission represent my own original technical administration work completed individually on my environment workstation.
---

## 6. Required Submission Details Block
*   **Repository Link:** https://github.com/Jakes-37/Oracle_pdb-II_20252SEN228_MULISA-Israel-Jakes
*   **PDB Name Created:** `JA_DB_20252SEN228`
*   **Issues Encountered:** Yes

