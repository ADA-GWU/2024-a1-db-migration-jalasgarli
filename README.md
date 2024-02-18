[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/JwSLLxUh)


# Database Migration README

## Introduction
This README provides instructions for migrating a PostgreSQL database schema and data according to specified requirements. The migration involves altering table structures and migrating data to meet the desired schema changes. Additionally, rollback procedures are outlined to revert changes if needed.

## Prerequisites
- Access to a PostgreSQL database instance.
- Permissions to alter table structures and migrate data.

## Backup Data
Before the migration process, it is important to back up the database to ensure data integrity. Perform a full backup using PostgreSQL's built-in tools or third-party backup solutions.

## Migration Steps:
1. **Alter Table Structure**:
    - Rename the `ST_ID` column in the `STUDENT` table to `STUDENT_ID`.
    - Alter the data type and length of the `ST_NAME` and `ST_LAST` columns in the `STUDENT` table from `STRING(20)` to `STRING(30)`.
    - Alter the name of the `INTEREST` column in the `INTEREST` table to `INTERESTS` and change its type to an array of strings.

2.  **Migrate Data**:
    - For the `STUDENT` table:
        - Update the `ST_ID` column to `STUDENT_ID`.
        - Alter the data type and length of `ST_NAME` and `ST_LAST` columns.
    - For the `INTEREST` table:
        - Group interests by `STUDENT_ID` and aggregate them into an array.

3. **Verify Migration**:
    After performing the migration, verify that the tables and data are in the desired state.

## Rollback Steps
1. **Restore from Backup**:
    If any issues arise during the migration or rollback process, restore the data from the backup made before the migration.

2. **Revert Alterations**:
    - Restore the original column names and types in the `STUDENT` and `INTEREST` tables.
    - Revert the data types and lengths of the `ST_NAME` and `ST_LAST` columns in the `STUDENT` table.
    - Rename the `INTERESTS` column back to `INTEREST` in the `INTEREST` table.

3. **Verify Rollback**:
    After rolling back the migration, verify that the tables and data are restored to their original state.

## Troubleshooting
- If any errors occur during the migration or rollback process, refer to PostgreSQL's documentation for troubleshooting steps.

## Conclusion
This README provides a comprehensive guide for migrating a PostgreSQL database schema and data, along with rollback procedures to revert changes if necessary. Following these instructions will help ensure a smooth migration process while minimizing the risk of data loss or corruption.
