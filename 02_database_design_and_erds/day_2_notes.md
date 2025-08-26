### 1. Basics of Database Design
- Why database design matters: performance, scalability, avoiding data duplication, ensuring consistency.
- Relational vs. non-relational databases (at least briefly — but ERDs are mostly for relational).
#### Normalization:
- 1st Normal Form (1NF): no repeating groups, atomic values.
- 2NF: no partial dependency on part of a composite key.
- 3NF: no transitive dependencies.
- Maybe Boyce–Codd Normal Form.
- Denormalization: why sometimes you don’t normalize for performance reasons.
### 2. Entities, Attributes, and Relationships
- Entities = things in your system (e.g., User, Order, Product).
- Attributes = the properties of those things (e.g., User.name, Order.date).
- Keys:
  - Primary keys (unique identifiers).
  - Foreign keys (linking tables).
  - Candidate keys, composite keys.
- Relationships:
  - One-to-one (1:1)
  - One-to-many (1:N)
  - Many-to-many (M:N, often resolved via a join table).
### 3. Entity–Relationship Diagrams (ERDs)
- Notation: crow’s foot, Chen notation, UML-like notations.
- How to draw: boxes for entities, lines for relationships, symbols to show cardinality.
- Examples:
  - A user can place many orders.
  - Each order contains many products (many-to-many).
  - Converting an ERD → actual schema (tables with foreign keys).
### 4. Designing for Real Use Cases
- Start from requirements → identify entities → draw ERD → refine relationships → map to schema.
- Tradeoffs between:
  - Simplicity vs. flexibility.
  - Normalization vs. performance.
  - Referential integrity vs. denormalization.
### 5. Advanced Topics (if time allows)
- Indexes: how they affect design and queries.
- Constraints: unique, not null, check constraints.

Cascade rules: what happens on delete/update.
Schema evolution: migrations, versioning.
ERD tooling: dbdiagram.io, Lucidchart, Draw.io, ERD features in SQL clients.
👉 In short: you’ll learn to take a real-world description of a system → identify entities → map relationships → normalize data → draw an ERD → turn it into a relational schema.

# Day 2

- normalization:
- - you should aim for 3rd normalization
  - the major pro is:
  - - reduce data redundancy
    - Major con:
      - performance cost.
- 1 to 1 tables we don't need to normalize.
  - for isntance address is not a top-level entity. Unless it's like a real-estate or a delivery app. But in most case adddress doesn't live in its own table. It can live in the users table.
  - "top-level entity" means a primary table that represents core-business logic.

- manager -> Employee ERD:

  - self referencial 1:M
  - book recommendation -> self referential M:M. rarely used but they exist.


### - interviews

- they want to see if you're someone they would want to learn with
- If they push you beyond your limits, t\it's good because it means they're trying to see your boundaries.
- SD ointerviewsa re different from the DSA interviews because there are mutliple correct answers.

### Functional system design
- the goal is to get to the ERD
- Start small -> 2/3 use cases
  - pick the easiest/commonest use cases
- services -> API end-points
  - POST /subreddits/:subredditId/posts body:postContent, userId
- sometimes they may even ask you to write some SQL statements (simple ones)

- 
- analytics
- How to handle discounts -> product discount, promo code (coupon), whole order. This is a typical question.
