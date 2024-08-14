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

###Books Table

CREATE TABLE books
(
   BookID NUMBER(10) PRIMARY KEY,
   title VARCHAR2(300),
   description TEXT,
   AuthorID NUMBER,
   FOREIGN KEY (AuthorID) REFERENCES authors(AuthorID)
);



Here's a GitHub README file for your SQL database project:

markdown
Copy code
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


### Books Table
CREATE TABLE books
(
   BookID NUMBER(10) PRIMARY KEY,
   title VARCHAR2(300),
   description TEXT,
   AuthorID NUMBER,
   FOREIGN KEY (AuthorID) REFERENCES authors(AuthorID)
);

### Sample Data
### Authors

INSERT INTO authors (first_name, last_name, nationality) VALUES
('John', 'Kani', 'South African'),
('Chinua', 'Achebe', 'Nigerian'),
('Haruki', 'Murakami', 'Japanese'),
('Markus', 'Zusak', 'Australian'),
('Salman', 'Rushdie', 'Indian');

### Books
INSERT INTO books (title, description, AuthorID) VALUES
('Things Fall Apart', 'This novel is a cornerstone of African literature, depicting the life of Okonkwo, a respected leader in the Igbo community, and the impact of European colonialism on traditional African society. It explores themes of cultural conflict, tradition, and change.', 2),
('The Wind-Up Bird Chronicle', 'This surreal and complex novel follows Toru Okada, a man searching for his missing wife, Kumiko, in a strange and unsettling version of Tokyo. Blending elements of fantasy, history, and existentialism, the book delves into the subconscious and the nature of reality.', 3),
('Midnight\'s Children', 'This Booker Prize-winning novel tells the story of Saleem Sinai, born at the exact moment of India’s independence. The novel is a blend of history and magical realism, exploring the turbulent history of modern India through the eyes of its protagonist.', 5),
('The Book Thief', 'Setting in Nazi Germany, this novel is narrated by Death and tells the story of Liesel, a young girl who finds solace in stealing books and sharing them with others. The novel is a powerful exploration of the impact of war, the power of words, and the resilience of the human spirit.', 4),
('Nothing but the Truth', 'The story explores the themes of truth, reconciliation, and the complex dynamics of family relationships in post-apartheid South Africa.', 1),
('Missing', 'This play is about an exiled South African politician living in Sweden who faces the challenges of reconciling his past with the present as South Africa undergoes changes after the end of apartheid.', 1),
('Kunene and the Kin', 'This is a more recent work that Kani co-wrote and starred in. The play is a poignant exploration of race, reconciliation, and the legacy of apartheid, set in the context of contemporary South Africa.', 1),
('The Golden House', 'Set in contemporary America, this novel explores themes of politics, identity, and power through the story of a wealthy, mysterious family.', 5),
('The Wind-Up Bird Chronicle', 'A complex tale of a man searching for his missing wife, which delves into history, dreams, and the subconscious.', 3);




Here's a GitHub README file for your SQL database project:


# SQL Database Project: Authors and Books

## Overview

This project involves creating and managing a relational database with two main tables: `authors` and `books`. The `authors` table contains information about authors, and the `books` table stores information about books and links them to their respective authors.

## Database Schema

### Authors Table


CREATE TABLE authors
(
    AuthorID NUMBER(10) PRIMARY KEY,
    first_name VARCHAR2(20),
    last_name VARCHAR2(20),
    nationality VARCHAR2(25)
);

### Books Table

CREATE TABLE books
(
   BookID NUMBER(10) PRIMARY KEY,
   title VARCHAR2(300),
   description TEXT,
   AuthorID NUMBER,
   FOREIGN KEY (AuthorID) REFERENCES authors(AuthorID)
);
### Sample Data
## Authors

INSERT INTO authors (first_name, last_name, nationality) VALUES
('John', 'Kani', 'South African'),
('Chinua', 'Achebe', 'Nigerian'),
('Haruki', 'Murakami', 'Japanese'),
('Markus', 'Zusak', 'Australian'),
('Salman', 'Rushdie', 'Indian');

### Books

INSERT INTO books (title, description, AuthorID) VALUES
('Things Fall Apart', 'This novel is a cornerstone of African literature, depicting the life of Okonkwo, a respected leader in the Igbo community, and the impact of European colonialism on traditional African society. It explores themes of cultural conflict, tradition, and change.', 2),
('The Wind-Up Bird Chronicle', 'This surreal and complex novel follows Toru Okada, a man searching for his missing wife, Kumiko, in a strange and unsettling version of Tokyo. Blending elements of fantasy, history, and existentialism, the book delves into the subconscious and the nature of reality.', 3),
('Midnight\'s Children', 'This Booker Prize-winning novel tells the story of Saleem Sinai, born at the exact moment of India’s independence. The novel is a blend of history and magical realism, exploring the turbulent history of modern India through the eyes of its protagonist.', 5),
('The Book Thief', 'Setting in Nazi Germany, this novel is narrated by Death and tells the story of Liesel, a young girl who finds solace in stealing books and sharing them with others. The novel is a powerful exploration of the impact of war, the power of words, and the resilience of the human spirit.', 4),
('Nothing but the Truth', 'The story explores the themes of truth, reconciliation, and the complex dynamics of family relationships in post-apartheid South Africa.', 1),
('Missing', 'This play is about an exiled South African politician living in Sweden who faces the challenges of reconciling his past with the present as South Africa undergoes changes after the end of apartheid.', 1),
('Kunene and the Kin', 'This is a more recent work that Kani co-wrote and starred in. The play is a poignant exploration of race, reconciliation, and the legacy of apartheid, set in the context of contemporary South Africa.', 1),
('The Golden House', 'Set in contemporary America, this novel explores themes of politics, identity, and power through the story of a wealthy, mysterious family.', 5),
('The Wind-Up Bird Chronicle', 'A complex tale of a man searching for his missing wife, which delves into history, dreams, and the subconscious.', 3);


### Queries
## Query 1: Total Number of Books

SELECT COUNT(*) AS SumOfBooks
FROM books;

## Query 2: Author with the Most Books
SELECT a.first_name, a.last_name, COUNT(b.BookID) AS authorBookCount
FROM authors a
LEFT JOIN books b ON a.AuthorID = b.AuthorID
GROUP BY a.first_name, a.last_name
ORDER BY authorBookCount DESC
FETCH FIRST 1 ROWS ONLY;


##Query 3: Number of Books by Nationality
SELECT a.nationality, COUNT(b.BookID) AS TheNumberOfBooks
FROM authors a
JOIN books b ON a.AuthorID = b.AuthorID
GROUP BY a.nationality;

