# ER Diagram To Relation Scheme Translation

- Each entity gets translated and represented as a relation
  - Everything will be translated as a relation
- Format for relation schema:
  - EntityType(<u>primaryKey</u>, foreignKey, attribute1, attribute2)

## Attributes

- Composite attributes will be removed and only the fundamental attributes will be stored
- But what about multi-valued attributes?

### Multi-Valued Attributes

- Create a new relation schema
- Include the multi-valued attribute
- Include as foreign key the primary key of the entity type it belongs to
- Choose as primary key of the new relation the composite of both attributes
- TL;DR
  - A new table is created with the value of the original entity, then also the primary key of the original entity kept in the new table as a foreign key

### Derived Attributes

- Do not need to be stored
- Trade off between
  - Time computing their values
  - Space storing them in the database

## Weak Entity Types

<!-- - Include all attributes together with the primary key of the parent entity type as foreign keys -->

- The primary key will be added as a foreign key to the weak entity type

## 1:M (1:1) Relationship Types

- The primary key of the `1` entity will be stored as a foreign key in any `M` entities
- If the two 1:1 entities have a "total" relation, you can merge the two entities
  - Total being it's a complete mapping where 1 row only references 1 other unique row of the other entity

## M:M Relationship Types

- Create an intermediary entity which stores the primary keys of both entities as foreign keys

## Ternary Relationship

- If there are `k` participating `1` entities, the primary key can be made up of `k - 1` can make up the primary key

## Logical Schema

- Entity constraints:
  - Primary keys can't be null
  - Not null constraints can be added where needed
- Document E.g

Staff(<u>staffNo</u>, Iname, branchNo)<br>
**PrimaryKey** staffNo<br>
