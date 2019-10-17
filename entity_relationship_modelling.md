# Entity Relationship Modelling

- For conceptual design/modelling
- Top-down approach
- Consists of identifying:
  - `Entities/entity types` objects/types of interest
  - `Relationships` associations/links between entities
  - `Attributes` properties of entities/relationships
  - `Constraints` on entities/relationships/attributes

## Entities (Of An Entity Type)

- Can be physical or abstract
- Belong to an entity type
  - Group with the same properties (e.g student, staff, product)

## ER Diagrams

- E/R models are often written as diagrams
- Entities are represented as boxes

## Relationships

- Are relationships between two or more entity types, e.g:
  - A branch employs staff
  - A student attends several classes

### Relationship Types

- Degree of a relationship type: number of entity types involved (degree employs is 2)

### Relationships In Diagrams

- links 2 entities together
- Represented as a diamond shape that connects entities by lines coming off the diamond where the name of the link in the diamond

## Attributes

- They are facts, aspects, properties or details about an entity or relationship
- E.g
  - Staff has a phone number, DOB, address
  - Branch has an address, manager (this may not be good, since the manager has many attributes themselves, so makes more sense to have a relationship rather than attributes)
  - Relationship "Employs" may have a start date for the employment

### Kinds Of Attributes

- Simple attribute
  - Has a **domain** in which its values are taken
  - May be **single-valued** or **multiple-valued**
    - May have several values for this attribute (e.g multiple phone numbers for work/home/personal)
- Composite attribute
  - Consists of multiple components each of which can be simple or composite again (e.g parts of an address)
- May be a **key attribute**:
  - Part of a group of attributes which uniquely identify entities
  - Primary key:
    - A single attribute which uniquely identifies an entity
  - Composite key:
    - A group of attributes which uniquely identity an entity
- Derived attribute
  - Represents a value that is derivable from the value of one or several other related attributes
  - E.g DOB and also age - age can be derived from DOB

### Key Attributes

- Keys consist of just one attribute like:
  - National insurance number
  - Membership number
  - Etc.
- These numbers uniquely identify a person/object
- But keys can also consist of several attributes:
  - A branch may be characterised by its postcode and the house number
- Occasionally there are several possibilities for a key

### Attributes In E/R Diagrams

- Names of attributes in ovals
- Attributes that make up composite attributes are represented as thicker lined ovals (e.g address could be made of street, town and postcode)
  - Then the attributes that make up the composite one will be coming off of it
- Also for relationships, avoid using "has" since it's ambiguous

#### Special Attributes In Diagrams

- Key attribute
  - Underlined in the oval
- Multiple valued attribute (I.e multiple attributes of the same thing, e.g phone numbers)
  - 2 ovals drawn around it
- Derived attributes
  - Broken line ovals

### Convention

- Not allowed to mix special attribute types so no attribute can be composite and multi-valued at the same time
- For entity types always use nouns starting with an uppercase letter (e.g class names)
- Relationships use verbs, all uppercase
