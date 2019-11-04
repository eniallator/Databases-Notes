# Normalisation

- Disallow anomalies by removing data redundancy
- What is it?
  - A technique for producing a set of relations with desirable properties, given the data requirements of an enterprise

## First Normal Form

- It's not yet about redundancy
- Each row must only contain one value for each column
- I.e no multi-valued attributes for each column
- Relations obtained by our translation from
  conceptual to logical design are automatically
  in 1NF

## Second Normal Form

- A relation in 1NF such that every non-primary-key attribute is fully functionally dependent on the primary key, is in 2NF

## Third Normal Form

- A relation that is in 2NF and in which no non-primary-key attribute is transitively dependent on the primary key is in 3NF

### Transitive Dependency

- If A -> B and B -> C, then C is transitively dependent on A via B

## Summary

- Every field in a record must depend on
  - The key, (1NF)
  - The whole key (2NF)
  - And nothing but the key (3NF)

## Keys

- Candidate keys
  - It can be used as a key
- Primary keys
  - Primary key attribute replaced by
    - Prime attribute: an attribute which is part of any candidate key

## General Definition Of 2NF/3NF

- 2NF:
  - A relation in 1NF such that every non-prime attribute is fully functionally dependent on all candidate keys, is in 2NF
- 3NF:
  - A relation that is in 2NF and for which no non-prime attribute is transitively dependent on some candidate key, is in 3NF

## Boyce-Codd Normal Form (BCNF)

- A relation is in BCNF, if and only if, every determinant of a full dependency is a candidate key
  - BCNF is a stronger form of 3NF
  - Can we have X -> A where A is a prime attribute and X is not a key?
    - Yes in 3NF, not in BCNF

## More Normalisation

- There is 4NF and 5NF
- In practice, many DBs are de-normalised to a certain extent

## Pros/Cons

- For online transactional DBs, one usually normalises to 3NF to avoid anomalies (OLTP)
- For onine analytical processing, where one works with "fixed" data it is advantageous to use de-normalised DBs because it's faster since there's no need to use joins (OLAP)
