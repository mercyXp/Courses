# Introduction to Database Technology

## 1. Overview

This document introduces the foundational ideas behind **Database Technology**, focusing on the concept of **Data Models** and their role in information systems. While this book only explores a portion of the broader topic, it emphasizes essential ideas for understanding and working with databases effectively.

---

## 2. What Is Database Technology?

According to the *Great Soviet Encyclopedia*:

> **Technology** is a collection of methods and processes used to obtain, process, or transform raw materials or products across industries; it is also a scientific discipline that develops such methods.

In the context of **information technology**, database technology refers to the structured approach to creating and managing **information systems** where a **Database Management System (DBMS)** controls long-term data storage using a **database**.

---

## 3. When Should You Use Database Technology?

Use database technology when the following conditions are met:

1. You need long-term storage of data about a **real or conceptual domain** (called a *subject area* or *SA*).
2. Multiple users need access to the data, including users who cannot perceive the real-world domain directly.
3. You require **structured storage**, not a disorganized data pile.
4. The domain is **dynamic** and requires updates by authorized users.
5. Most users will retrieve and transform information through a system interface.
6. Derived data should be created through **simple, universal operations**, not custom algorithms.
7. Information is primarily represented in **text and numeric formats**.

By the end of this book, readers will be able to evaluate whether database technology is appropriate for a given scenario.

---

## 4. Key Features of Database Systems

Database systems typically use a **data model (DM)** — a structured way to describe:

- **Objects** in the real world
- **Relationships** between them

### Common Components of a Data Model:

- Rules for valid **data structures**
- Rules for **data integrity**
- A set of **data operations**

These models help form the **database schema** and ensure data can be effectively stored, modified, and queried.

---

## 5. Terminology Note

In traditional sciences, a **model** is a representation based on a theory. In database technology, however, the term *"model"* refers to the theory itself — and the result of modeling is the **database**. This terminology evolved historically and is widely accepted, though unconventional.

---

## 6. Example: The Relational Model

The **relational model** uses **tables (relations)** to structure data:

- Each table represents an **object type** (e.g., `Person`).
- Each column is an **attribute** (e.g., `Name`, `Age`).
- Column headers define the structure of the data.

### Schema Definition

Before any data is entered, a **schema** must be defined. For example, the `Person` table might include:

| Name | Age | Height |
|------|-----|--------|

### Integrity Constraints

Rules ensure data consistency, such as:

> "Height must be a whole number between 50 and 300."

These constraints help avoid errors but do not replace human judgment about what data is accurate.

---

## 7. Data and Interpretation

The DBMS keeps track of the **structure** and **meaning** of the data:

- Each value is connected to a table and column.
- This **interpretation** transforms raw data into useful **information**.

Without headers and labels, data becomes a meaningless sequence of symbols.

---

## 8. Why Data Models Matter

Data models are essential for:

- Understanding what data **means**
- Organizing data effectively
- Supporting structured **data processing** and **retrieval**

In short, **data models are the key to turning data into actionable information**.

---

[DB-sYSTEM](https://github.com/mercyXp/Courses/blob/main/1.Databases/a.Book-on-Data-Models(by%20Babanov)/img/DB_tech.png)

The image above outlines the main processes involved in database (DB) technology and its participants—both human and system-based. It serves as an introduction to key concepts, roles, and workflows within the lifecycle of a database system.

---

## 📌 Key Concepts

### 🧩 DB Participants and Processes

- **Participants:** Include both people and software/hardware components.
- **Optional Processes:** Development of specialized software for domain-specific business logic. These are not the focus of this course because:
  1. They are optional if users interact with the DB using general-purpose dialog tools.
  2. They fall under general-purpose programming technologies (e.g., Java, C#, Visual Basic).

---

## 🧍 Human Roles in DB Systems

- Represented by stylized figures in diagrams.
- Multiple individuals may share a role (e.g., DB Admin department).
- In small personal systems, one person may fulfill all roles.

---

## 🖥️ System Components

- **Rectangles in diagrams** represent software/hardware tools.
- They manage data in main and long-term memory.
- They also coordinate interactions between participants.

---

## 🔁 Information Flows

- **Arcs with arrows** indicate data flow directions between people and systems or between systems.
- **Cylinders** inside rectangles symbolize long-term storage (usually hard drives) managed by the DBMS.

---

## 📐 Database Schema Design

### Importance:
- The **most critical and mandatory** process.
- Largely determines the ease of implementation and system success.

### Process Overview:
1. **Study the domain** (independently and with experts).
2. **Formalize knowledge** into a **semantic schema** using an appropriate **semantic data model**.
3. **Select a model** with:
   - High expressive power.
   - CASE tool support for automatic translation into DBMS models.

---

## 🧠 Semantic Schema Design

- Captures domain rules and structures.
- Should avoid reliance on natural language or weak models.
- If CASE tools are unavailable:
  - Translation must be done manually.
  - Designer needs to know conversion methodologies.

> ✅ Better to use a strong semantic model without CASE than a weak model with poor CASE tools.

---

## 📚 Translation to Relational Model

- We'll explore:
  - Several semantic models.
  - Methods for translating them into relational models (used by most DBMSs).

---

## ⚙️ System Installation and Administration

- After schema and dialog system development, the **DBA** installs the system on customer infrastructure.
- The DBA:
  - Administers at the **physical schema level**.
  - Ensures continuous and efficient operation.
- Admin responsibilities are **outside the scope** of this document.

---

## 👥 System Use by End Users

- Users act as:
  - **Writers**: Update the DB with domain changes.
  - **Readers**: Query the DB for information.
- This is the **main ongoing process** during the system’s operation.
- **Simplicity is key**: Dialog tools hide system complexity from users.
- We'll introduce some **data manipulation languages**, mostly for advanced users.

---

- The success of a DB system heavily relies on a **well-designed schema**.
- Semantic models and CASE tools are crucial for efficient design and translation.
- Users interact with the system in intuitive ways, while complexity remains under the hood.

---
# Evolution and Architectures of Database Systems

[image needed here]

## Introduction

Databases were initially used in large corporations and organizations as the foundation for large transaction processing systems.

> **Note**: The term **“transaction”** was once used strictly for banking transfers, but now refers to any form of data transfer in information systems. In DB technology, the word has a special technical meaning that will be covered later.

## Mainframe-Based Systems

Originally, database systems were run on **mainframes** — large, centralized computers that multiple users accessed via terminals. The DBMS would run on the mainframe and interact with users through those terminals.

This architecture is now largely obsolete and resembles a **single-user setup**, as all processing is done by one computer.

## Single-User Architecture

As **microcomputers** became more common, DB systems were adapted for **personal and single-user applications**. In this architecture:

- The **DB**, **DBMS**, and **user interface** all run on one computer.

## Multi-User Architecture & Local Networks

As microcomputers began networking into **workgroups**, database technology evolved to support **multi-user architectures**.

Differences from mainframe-based systems include:

- Use of **multiple processors** (not just one).
- Greater **performance**, but also increased complexity in coordination.

This led to the development of **client-server architecture** for databases.

## Client-Server Architecture

Unlike the single-user model, client-server systems involve **multiple computers connected via a network**:

- **Clients**: Run application software and interface with users.
- **Servers**: Handle database operations.

Both clients and servers are usually **microcomputers** due to cost-efficiency.

### Server Configurations

- Typically, there is **one DB server**, but not always.
- If multiple servers manage **different databases**, it’s still client-server.
- If multiple servers manage **a single database**, it’s called a **distributed database system**.

## Internet & Intranet Applications

Modern database systems are widely used in **web applications**, employing a **three-tier architecture**:

1. **Database Server**
2. **Web Server**
3. **Browser (Client)**

Each tier may run on a separate computer with its own OS, though they can all reside on one machine.

### Data Flows

- **SQL commands & relational data**: DB server ↔ Web server
- **Web pages, client scripts, etc.**: Web server ↔ Browser

## Component Responsibilities

### Database Server

- Hosts the **DBMS**
- Executes **SQL commands**
- Manages the **database**

### Web Server

1. Accepts and responds to **HTTP requests**
2. Executes **business logic**
3. Sends and receives **SQL queries** from/to the DB server

### Browser

1. Acts as an **HTTP client**
2. Runs **client-side scripts**
3. Renders content from **HTML/markup**

## Application Server Layer

In diagrams, the middle tier is labeled **“Application Server”**, a broader term than “Web Server.”

> Three-tier systems can be built using non-web technologies as well.

### Transaction Processing Monitors (TPMs)

**TPMs** are software systems for managing **distributed transactions** in a scalable and efficient way.

#### Key Features:

- Scalability
- Full functionality
- Data integrity
- High performance at low cost
- Support for heterogeneous environments

TPMs rely on the **three-tier client-server model**.

### Leading TPMs:

- **ACMS** (DEC)
- **CICS** (IBM)
- **TOP END** (NCR)
- **PATHWAY** (Tandem)
- **ENCINA** (Transarc)
- **TUXEDO** (USL)

---
# Transactions, OLTP, OLAP, and Data Warehousing

## What is a Transaction?
A **transaction** is a logically indivisible unit of data operations (usually involving multiple operations on a database) that must be executed atomically. A database system guarantees that either all operations in a transaction are successfully completed and committed to the database, or none of them are, in the event of a system failure before the transaction finishes.

Thus, a transaction is either fully completed or fully rolled back, as if it never occurred.

## Online Transaction Processing (OLTP)
Initially, database management systems (DBMS) were designed to handle a high volume of transactions, each involving minor changes to the operational data of an enterprise. These systems are known as **Online Transaction Processing (OLTP)** systems.

- OLTP databases can range in size from a few megabytes to several gigabytes, and in some cases, even up to terabytes or petabytes.
- This document focuses mainly on database technology applications for OLTP systems.

## The Need for Analytical Access
Corporate decision-makers need access to all organizational data, regardless of location. To thoroughly analyze business performance, trends, and demand characteristics, access is required not only to current but also to **historical** data.

## Data Warehousing
To facilitate such analysis, the **data warehouse** concept was introduced. A data warehouse (an analytical database) aggregates information from various sources, including operational databases, and stores cumulative and summary data.

Decision-makers require powerful tools to analyze the data stored in warehouses. In recent years, the main tools used for this purpose are **Online Analytical Processing (OLAP)** tools.

## Online Analytical Processing (OLAP)
**OLAP** defines an architecture that supports complex analytical applications:

- Most OLAP applications are based on **specialized multidimensional DBMSs** with structured datasets and customizable user interfaces.
- OLAP servers use **multidimensional structures** to store data and relationships, often represented as **data cubes**.

### Multidimensional Cubes
- A data cube is visually rendered in dynamic tables.
- Data is laid out across two axes: rows and columns. Sometimes a third axis is used with tabs or layers representing different tables.
- Each axis can represent one or more dimensions, with all combinations shown if multiple dimensions are present.

**Cube Cells**: Represent measurable values (e.g., money, kilograms, meters).

**Dimension Members**: Possible values within a dimension, which may form a hierarchy (e.g., day → week → month).

### Interactive Tools
OLAP tools allow users to dynamically build various projections and slices of the cube using:

- **Drag and Drop** – for rearranging elements
- **Drill-down and Drill-up** – for moving between levels of detail in dimension hierarchies

This enables users to independently and quickly gain different insights into the analysis objects, without needing programmers.

## OLTP vs. OLAP
The fundamental differences between OLTP and OLAP tasks are so significant that using the same DB and DBMS for both is often inefficient. Therefore, it is generally recommended to use specialized databases and management systems tailored to each purpose.

---

[IMAGE]

Here is the English translation of your text:

---

### Purpose and Structure of the Course

The goal of this lecture course is to provide a deep understanding of the fundamentals of data modeling in database (DB) technology, to study the main data models widely used in practice, and to master the methods of designing database schemas.

The logic and sequence of the material are determined by this goal and the chain of transformations that data representations undergo—from the objective reality to the database stored in a computer's memory. This multilayered "cake" of representations is shown on the left side of the diagram (referred to in the original text).

On the right side, across horizontal layers, are listed the scientific and technical fields corresponding to each level of representation, the appropriate software tools, and specific data models. If a formal system exists for a given level (the highest form of theory), it is noted in the far-right column.

The **Subject Area (SA)** is a particular fragment of the real or ideal world of interest to the DB system's customer. Initial representations of the SA arise in the mind of the DB designer, based on personal familiarity and input from domain experts or other sources. These initial representations are entirely informal and consist of visual, auditory, olfactory, and tactile impressions.

By learning different data models, the designer becomes equipped with the formal concepts of each model. Their task is to translate their informal understanding of the SA into the language of a specific data model using its formal conceptual framework.

**Semantic data models** are closest to human ways of understanding the world, making this translation process easiest. The result is a **semantic schema** of the SA—its first formal representation. However, since there are no DBMSs that directly support semantic models, and the goal is ultimately to implement the database, we must go further.

Although DBMS-specific data models vary, they often share common features that form what are called **DBMS-oriented data models**. The most popular among these today is the **relational model**. If you choose a relational DBMS, you must construct a **relational schema** of your SA, which is a type of DBMS-oriented schema.

Each DBMS offers its own **dialect** of the DBMS-oriented data model, so ultimately, the SA schema must be expressed in that dialect. It's also important to note that each DBMS has **two data models**: logical and physical.

- The **logical model** is user-facing (intended for the designer or DB user) and provides languages and tools for communication.
- The **physical model** is mostly known only to the DBMS developers, as it deals with how data is stored in memory and on disk.

Naturally, these models define the **lowest-level representations** of the SA: the **logical and physical schemas** of the DB. The structural concepts of these models are not easy to grasp (they are primarily for professionals), as everything is focused on efficient memory usage and query response time.

---

# Data Modeling in Database Technology

## Course Objective

The purpose of this course is to provide a deep understanding of:

- The fundamentals of **data modeling** in database technology.
- The main **data models** widely used in practice.
- Techniques for **designing database schemas**.

---

## Course Structure and Logic

The sequence of the material reflects the process of transforming knowledge about a subject area (SA) from **objective reality** into a **database** stored in a computer. This transformation is illustrated as a **multi-layered system of representations**, each corresponding to a specific scientific field, software tool, and data model.

---

## From Reality to Database

### Subject Area (SA)
The SA is a fragment of the real or ideal world relevant to the database system. The designer initially builds a mental model based on personal experience and input from experts. These early impressions are informal—visual, auditory, tactile, etc.

### Semantic Data Models
To formalize understanding, designers use **semantic data models**, which align closely with human cognition. These models allow the creation of a **semantic schema**—the first formal representation of the SA.

> **Note**: Semantic models are not directly supported by DBMSs. To implement a database, further translation is required.

---

## DBMS-Oriented Data Models

Most DBMSs use **DBMS-oriented models**, such as the **relational model**, which is currently the most popular.

If you're using a relational DBMS, you will need to design a **relational schema** for your SA. Each DBMS has its own **dialect**, so your schema must conform to that dialect.

---

## Two Layers of DBMS Models

Every DBMS provides **two types of data models**:

1. **Logical Model**  
   - Designed for human interaction.
   - Provides languages and tools for querying and schema design.

2. **Physical Model**  
   - Focuses on data storage in memory and on disk.
   - Mostly relevant to DBMS developers.

These define the **logical and physical schemas** of the database.

---

## Key Considerations

- **Semantic models** make it easier to conceptualize and understand the subject area.
- **Relational and DBMS-specific models** are necessary for implementation.
- **Logical models** serve the user.
- **Physical models** ensure efficiency in storage and query processing.

---

In the final part of the introduction, we announce the material presented to the reader. The structure of the course reflects its logic.

In the chapter "Basic Concepts," we will introduce the key terms of data modeling, define the concept of a "data model," and its components—rules for data structuring, integrity constraints, and a variety of operations on the data. In subsequent chapters, the analysis of specific models will follow the "structure – integrity constraints – operations" schema.

In the chapter "Semantic Data Models," we will explore the ER model and ERM model, as well as the methodology of semantic modeling for the ERM model.

The chapter "DBMS-Oriented Data Models" is almost entirely dedicated to the relational model, which is remarkable in many aspects and widely used today. In the final paragraph of the chapter, we will review the classical methodology for designing relational database schemas. This methodology is distinctive in that it explicitly omits the intermediate representation of the subject area in the form of a semantic schema.

Finally, the essence of the course is presented in the chapter "Semantic Methodology for Designing Relational Database Schemas," which explains how to practically solve the task of designing database schemas. To fully understand this chapter, it will be necessary to use practically all of the previous material from the book, so it is recommended that by this point, you have a solid, consistent system of knowledge on data models.

### Questions and Tasks for Chapter 1

1. What are the distinctive features of database technology that set it apart from other technologies, especially information technologies?
2. What are the prerequisites for using database technology?
3. What is the significance of the term "model" in database technology?
4. What is the main purpose of data models?
5. List the components of any data model.
6. What is the purpose of data structures, integrity constraints, and operations on the data?
7. Identify the main processes in DBMS, and explain who is responsible for which tasks.
8. What are CASE systems used for?
9. List and briefly characterize the architectures of DBMS systems.
10. What are the main differences between OLTP and OLAP DBMS?
11. What forms of representations of the subject area are distinguished in database technology? Characterize each one.

---

 


> This course will guide you through each of these layers and help you master the skills required to model, design, and implement a database from scratch.


> _This document is part of a broader study on DBMS theory and practice, with a focus on schema design and semantic modeling._

