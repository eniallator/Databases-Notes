# SQL

## Multi-Column Constraints

- When multiple columns are used for a primary/alternative key they use a table constraint:
  - `PRIMARY KEY (<col-name-1>, ..., <col-name-n>)`
  - `UNIQUE (<col-name-1>, ..., <col-name-n>)`
  - `FOREIGN KEY (<col-name-1>, ..., <col-name-n>) REFERENCES <table> (<rcol-1>, ..., <rcol-n>)`

### Multi-Column Examples

```sql
CREATE TABLE Client (
  clientNo INT PRIMARY KEY, ...
);
CREATE TABLE Property (
  propId CHAR(6) PRIMARY KEY, ...
);
CREATE TABLE Viewing (
  clientNo INT,
  propId CHAR(6),
  viewDate DATE NOT NULL,
  CONSTRAINT fk_client_in_viewing
  FOREIGN KEY(clientNo) REFERENCES Client(clientNo),
);
```

## Dropping/Altering Tables

- Dropping:

````sql
DROP TABLE [IF EXISTS] <tab-name>;```
````

- Altering:

```sql
ALTER TABLE <tab-name>;
```

- Different ways:

```sql
ADD [COLUMN] <column-def> |
ADD [CONSTRAINT <name>] <constraint-def> |
DROP [COLUMN] <column-name> |
DROP FOREIGN KEY <key-name> |
DROP PRIMARY KEY |
MODIFY [COLUMN] <column-def>;
RENAME TABLE <current-name> TO <new-name>;
```

### Drop/Alter Examples

```sql
CREATE TABLE Staff (
  id_number INTEGER UNSIGNED,
  city VARCHAR(15)
);
ALTER TABLE Staff MODIFY city VARCHAR(10);
```

- This may cause issues since the old values could be greater than 10 characters long

```sql
ALTER TABLE Staff
MODIFY city VARCHAR(20) NOT NULL;
```

- Adding a constraint can cause problems with existing data so there could be null data in the example above

```sql
ALTER TABLE Staff ADD CONSTRAINT myconstraint PRIMARY KEY(id_number);
```

- id_number may not be unique already
- id_number before could have been null as well

## Inserting Data Into Tables

- Insert values for all the attributes

```sql
INSERT INTO <tab-name>
  VALUES (<value-1>, ..., <value-n>), ...,
         (<value-1>, ..., <value-n>);
```

- Example

```sql
INSERT INTO Branch
VALUES (3, 'Oxford St. 5', 'London', 'W1CA2'),
       (6, 'foo rd', 'bar', 'baz');
```

- Insert values into a selected column

```sql
INSERT INTO <tab-name>(<col-1>, ..., <col-n>)
     VALUES (<value-1>, ..., <value-n>), ...,
            (<value-1>, ..., <value-n>);
```

## Updating Tables

- Allows a row in the table to be modified

```sql
UPDATE <tab-name>
SET <col-name-1> = <value-1>,
    ...
    <col-name-n> = <value-n>
  [WHERE <cond>];
```

- If the where clause is omitted, all rows are updated

### Conditions

- Comparison:

```sql
<exp> >|=|<|<> (aka !=)|<=|>= <exp>
```

- Range:

```sql
<exp> [NOT] BETWEEN <exp> AND <exp>
```

- Membership test:

```sql
 <exp> [NOT] IN (<val-1>, ..., <val-n>)
```

- Pattern match:

```sql
<string-exp> [NOT] LIKE <string-exp>
```

- `%` represents any string of characters
- `_` represents one character (wildcards)
- Test for Null

```sql
<col-name> IS [NOT] NULL
```

## Deleting From Tables

- Allows one of more rows to be deleted from a table

```sql
DELETE FROM <tab-name>
  [WHERE <cond>]
```

## More Types For Column Definitions

- User-defined types:
  - Enumeration
    - `ENUM (<string-1>, ..., <string-n>)`
  - Set types
    - `SET (<string-1>, ..., <string-n>)`
- Example

```sql
CREATE TABLE Car (
  colour ENUM('red', 'blue', 'green'),
  accessories SET('alloy wheels', 'stripes', 'roof rack')
);
INSERT INTO Car VALUES('red', '');
INSERT INTO Car VALUES('red', 'alloy wheels, roof rack');
```

- Don't use spaces in between the `SET` values

### Character Sets And Collation

- Can be set explicitly
- Character sets are e.g `latin1`, `hebrew`, `utf-8`
- Default character set for us seems to be `latin1`
- Collation refers to the various ways strings can be compared and ordered
