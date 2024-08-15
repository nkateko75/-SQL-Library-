# SQL Database Project: Authors and Books

## Overview

This project involves creating and managing a relational database with two main tables: `authors` and `books`. The `authors` table contains information about authors, and the `books` table stores information about books and links them to their respective authors.


## Step 1: Create Table  

The aim is to create a script that can be executed to create all the tables we need.	  

1. Books  
**Each book has the following attributes/columns: Title, Description, An author, Book Id.**

**Creating books' database**

CREATE DATABASE myBooks;

**Creating Books table**

CREATE TABLE books
(book_id INT PRIMARY KEY auto_increment,
title VARCHAR(100),
description  TEXT(300),
author_id INT,
FOREIGN KEY (author_id) REFERENCES authors(author_id));

**Inserting data into the authors table**

INSERT INTO authors VALUES

(1, 'John', 'Kani', 'South African'),
(2, 'Chinua', 'Achebe', 'Nigerian'),
(3, 'Haruki', 'Murakami', 'Japanese'),
(4, 'Markus', 'Zusak', 'Australian'),
(5, 'Salman', 'Rushdie', 'Indian');




###### Output

![image](https://github.com/user-attachments/assets/d6d37b57-f091-45ad-aa6f-5d4a043267df)


2. Authors  
**Each author has the following attributes:  First name,  Last name,  Nationality (this is an enumeration), Author Id.**

 CREATE TABLE authors
 
(
author_id INT PRIMARY KEY auto_increment,  

first_name VARCHAR(30),

last_name VARCHAR(30),

nationality ENUM ('South Africa', 'Australia', 'India', 'Nigeria', 'Japan') 
);
 
  
###### Output
![image](https://github.com/user-attachments/assets/71b90404-2e76-404f-9ed1-d89bacc2c516)




#### Step 2: Insert data.  

#### Create atleast 5 authors.  

**Write a script that populates your database.**

INSERT INTO authors VALUES

(1, 'John', 'Kani', 'South African'),
(2, 'Chinua', 'Achebe', 'Nigerian'),
(3, 'Haruki', 'Murakami', 'Japanese'),
(4, 'Markus', 'Zusak', 'Australian'),
(5, 'Salman', 'Rushdie', 'Indian');


###### Output 
![authors](https://github.com/user-attachments/assets/ace6d72f-1029-4a40-a8d7-93b6205fd822)

#### Create atleast 10 books.

**Inserting data into the books table**

INSERT  INTO books VALUES 

(1,'Things Fall Apart', 'This novel is a cornerstone of African literature, depicting the life of Okonkwo, a respected leader in the Igbo community, and the impact of European colonialism on traditional African society. It explores themes of cultural conflict, tradition, and change.', '2'),

(2,'The Wind-Up Bird Chronicle', 'This surreal and complex novel follows Toru Okada, a man searching for his missing wife, Kumiko, in a strange and unsettling version of Tokyo. Blending elements of fantasy, history, and existentialism, the book delves into the subconscious and the nature of reality.', '3'),

(3,'Midnight\'s Children', 'This Booker Prize-winning novel tells the story of Saleem Sinai, born at the exact moment of India’s independence. The novel is a blend of history and magical realism, exploring the turbulent history of modern India through the eyes of its protagonist.', '5'),

(4,'The Book Thief', 'Set in Nazi Germany, this novel is narrated by Death and tells the story of Liesel, a young girl who finds solace in stealing books and sharing them with others. The novel is a powerful exploration of the impact of war, the power of words, and the resilience of the human spirit.', '4'),

(5,'Nothing but the Truth', 'The story explores the themes of truth, reconciliation, and the complex dynamics of family relationships in post-apartheid South Africa.', '1'),

(6,'Missing', 'This play is about an exiled South African politician living in Sweden who faces the challenges of reconciling his past with the present as South Africa undergoes changes after the end of apartheid.', '3'),
(7,'Python', 'Code with the best', '1'),

(8,'Kunene and the King', 'This is a more recent work that Kani co-wrote and starred in. The play is a poignant exploration of race, reconciliation, and the legacy of apartheid, set in the context of contemporary South Africa.', '1'),

(9,'The Golden House', 'Set in contemporary America, this novel explores themes of politics, identity, and power through the story of a wealthy, mysterious family.', '5'),
(10,'The Wind-Up Bird Chronicle', 'A complex tale of a man searching for his missing wife, which delves into history, dreams, and the subconscious.', '3');


###### Output
![books](https://github.com/user-attachments/assets/49bf1619-7f0c-44fc-8ac4-9eb75dee7d4c)


  
##  Queries

#### Query 1: Total Number of Books

**Counts how many books there are in total.**

SELECT COUNT(*) AS total_books FROM books;


###### Output
![total books](https://github.com/user-attachments/assets/2da46799-4724-4eb8-bcd5-52c970464b3b)



#### Query 2: Author with the Most Books

**Determine which author has most books.**

SELECT A.first_name, A.last_name, COUNT(B.book_id) AS number_of_books
FROM authors A
JOIN books B ON A.author_id = B.author_id
GROUP BY A.author_id
ORDER BY number_of_books DESC
LIMIT 1;

###### Output
![most books](https://github.com/user-attachments/assets/b37e5061-345e-45eb-8656-85274ef4acd9)

#### Query 3: Number of Books by Nationality
SELECT A.nationality, COUNT(B.Book_id) AS number_of_books
FROM authors A
JOIN books B ON A.author_id = B.author_id
GROUP BY A.nationality;

###### Output
![nationality](https://github.com/user-attachments/assets/d8666933-c62e-451a-9513-3e976095652e)

