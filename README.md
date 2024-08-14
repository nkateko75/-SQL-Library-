# SQL Database Project: Authors and Books

## Overview

This project involves creating and managing a relational database with two main tables: `authors` and `books`. The `authors` table contains information about authors, and the `books` table stores information about books and links them to their respective authors.

## Database Schema

### Authors Table

```sql
CREATE TABLE authors
(
    AuthorID NUMBER(10) PRIMARY KEY,
    first_name VARCHAR2(20),
    last_name VARCHAR2(20),
    nationality VARCHAR2(25)
);
