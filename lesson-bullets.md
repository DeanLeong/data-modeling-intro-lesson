---
title: Intro to Relational Data Modeling
type: lesson
duration: "1:25"
creator:
    name: Micah Rich
    city: LA
competencies: Databases
---

# Intro to Relational Data Modeling

## Objectives

- Describe the relationship between tables, rows and columns
- Draw entity relationship diagrams with crow's foot notation for ideas for web apps
- Describe how tables relate to each other using foreign keys
- Explain the different relationship types – has_many_through, has_and_belongs_to_many, belongs_to

## Preparation

- Describe how objects have attributes and functionality associated with them

## Review: What is a Relational Database

- Relational database is a section of one or more hard drives where data is stored
- CRUD - create, read, update, delete/destroy
- Two types of databases:
    - relational (SQL)
    - document-based (NoSQL)
- Relational database allows for highly structured (normalized) data
- Relational database describes relation between conceptual entities (relations, aka tables: "Customer", "Product", "Order")

## Entity Relationship Diagrams (ERDs)

> ![crows foot notation cheat sheet](https://www.vivekmchawla.com/content/images/2013/Dec/ERD_Relationship_Symbols_Quick_Reference-1.png)

### Benefits of relationships
    - data lives (and is updated) in just one place
    - data from one relation can be shared with any other relation (via primary key/foreign key relationship)

## Three kinds of relationships:
- One to One:
    - uncommon.  Anj additional field/attribute in one table often makes more sense
- One to Many:
    - most commmon
    - has_many (belongs_to) (Customer, Order)
- Many to Many:
    - has_many (has_many) (Order, Product)


### Social Media Platform ERD

Working with a partner and working on a whiteboard, draw the ERD for a social media platform

- MVP: Posts, Comments, Users
- Bronze: Favorites/Likes
- Silver: Friends
- Gold: Sub-comments

## ERD to Schema

The next step after we are confident with our ERD is to write a schema based off of that ERD which will define our database tables.

Keep in mind that we learn more about our application and the demands of our application change over time. The schema is not set in stone forever but "migrating" a database that is in use can be both tricky and high stakes so it is important that we have thought hard about our schema design.

We won't worry about migrations in this unit -- it is easier for us to just rewrite our schema and dump our data since we are not working on live apps. At work however, the production database will hold data that is extremely valuable to your company. It will be important to make sure that data is not lost if the structure of the database changes and that changes don't cause interuptions to data collection. We will look at tools that make migrations much easier to manage in the final unit.

### Students, Classes, Instructors

- A student `has_many` classes and a class `has_many` students.
- A class `belongs_to` an instructor and an instructor `has_many` classes.

### Social Media Platfrom

Build out your ERD

## Conclusion (5 mins)

- How do you represent a relational database in drawings? How would you describe the metaphor of storing data like a spreadsheet?
- What are the three types of relationships we have discussed today, and what are some examples of how you would you use them?
