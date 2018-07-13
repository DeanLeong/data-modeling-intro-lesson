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

A database is a place where information gets stored in a hard drive - or distributed across multiple hard drives - on a computer somewhere. Much like we've been creating and storing data, here and there, a database represents a collection of individual pieces of data stored in a highly structured and searchable way; they represent a model of reality, which why we call them models in MVC.

Inside a database, we do basic actions like create, read, update, and destroy data – hey look, CRUD!

In modern web development, we think of databases in two categories: relational databases and NoSQL databases. We will focus on relational databases in this course. Relational databases impose more restrictions on how we model our data but these restrictions have payoffs in speed of access and integrity of data at scale. Our primary hurdle in structuring our relational databases is describing the relations between different tables.

When describing data with JavaScript objects, we can "nest" resources (e.g. A `class` object could have properties `instructor` and `students`, instructor being an object that describes the instructor and `students` being an array of objects representing students). NoSQL databases let us structure our data in this way so it's closer to an intuition we may already have, but we need to make many more considerations about how we are going to access our data when deciding its appropriate structure.

Relational databases impose some restrictions where we do not (though PostgreSQL does permit it) nest data. Instead we associate records using `primary` and `foreign` keys. This can be approach can feel counter intuitive at first but will become more natural with practice.

Consider the following Entity Relationship Diagram (ERD) for a school (especially consider the relationships between `class`, `student`, and `instructor`)

## Entity Relationship Diagrams (ERDs)

> ![crows foot notation cheat sheet](https://www.vivekmchawla.com/content/images/2013/Dec/ERD_Relationship_Symbols_Quick_Reference-1.png)

Relationships happen when we start seeing multiple duplicative information or when one object needs to "connect" to another object.

There are 3 different kinds:

### One to One

- not frequently used
- A student `has_one` SSN, and a SSN `belongs_to` a specific student - that lets us look up solely by SSN, and see the connected student
- Often, in situations like that, you can make the SSN an attribute of the student, but when the associated resource has, for example, multiple fields (e.g. an address), it might make sense to create another table for addresses and set up a `has_one` relationship

### One to Many

- the most common type of database relationship
- an university `has_many` classes, but a classes `belongs_to` only one university

### Many to Many

- also very frequent
- a student probably `has_many` classes, and a class also probably `has_many` students

Keep in mind, the `belongs_to` part always goes on the opposite side of the `has_many` or `has_one`. And the way it's stored is that the ID of the model that "has" something is stored in a field on the child, like "university_id".  In our example with university and classes, the class model `belongs_to` the university model, while the university `has_many` classes.

### Cheesy SQL Refactor (We do)

In the [cheesy SQL exercise](https://git.generalassemb.ly/wdi-nyc-lambda/cheesy-sql-exercise), we made a `cheese` table with properties **name**, **color**, **origin**, and **stink_level**.

#### Adding a table

Our cheeses have some repetition in the **origin** property.

- What would it look like to create a `region` table that was seperate from the `cheese` table?
- Which table references which?
- What kind of relationship is this?
- Why might we prefer this structure?

#### Multi-origin

This is better but we are still limited to a cheese being produced in only a single region.

- Can we go a step farther and structure our tables in a way that a single cheese can have more than one origin?
- What do we need to add/change to fascilitate this?
- What is the relationship between cheeses and regions after this update?

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

### Cheeses and Regions

- A cheese `has_many` regions and a region `has_many` cheeses
- NOTE: we have terms `origin` and `region`, aliasing can make things tidier

### Social Media Platfrom

Build out your ERD

## Conclusion (5 mins)

- How do you represent a relational database in drawings? How would you describe the metaphor of storing data like a spreadsheet?
- What are the three types of relationships we have discussed today, and what are some examples of how you would you use them?
