# Operations On Relations

- Tables can be constructed from old ones

## Operators On Relations

- Selection
- Projection
- Cartesian Product
- Union
- Intersection
- Set difference
- Natural Join, Theta-Join and Equijoin
- Rename

### Selection

- Select rows using a condition where they are placed into a table
- Uses a sigma symbol

### Projection

- Show only chosen columns on the table
- Uses the pi symbol

### Cartesian Product

- R x S is the relation containing the
  concatenation of every tuple of relation R
  with every tuple of relation S
- If relation R contains I tuples with N
  attributes, and S contains J tuples with M
  attributes, the Cartesian product will
  contain I\*J tuples with N+M attributes

### Joins

- Are notoriously difficult to implement (slow to run as well)
- Join data across tables
- Made from cartesian product and selection
- We use notation R.a to denote column a in
  table/relation R

#### Theta Join

- F is a predicate of the form R.a<sub>i</sub> theta<sub>i</sub> S.b<sub>i</sub> (for each i) where each theta<sub>i</sub> is a comparison operator (!=, =, <, >, <=, >=) so R.a<sub>i</sub> and S.b<sub>i</sub> must have a matching type

#### Equijoin

- Is a special type of theta join
- F is a prediccate of the form R.a<sub>i</sub> and S.b<sub>i</sub> so they must have a matching type

#### Natural Join

- If there are column names with the same names, then they must have the same values and so it will merge the values of the 2 separate columns
