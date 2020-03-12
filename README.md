# Certification_70-483
Certification 70-483 learning path

## Parallel LINQ

The AsParallel method examines the query to determine if using a parallel version would speed it up. If it is decided that executing elements of the query in parallel would improve performance, the query is broken down into a number of processes and each is run concurrently. If the AsParallel method can’t decide whether paralleli?ation would improve performance the query is not executed in parallel.

Ex:
```
var result = from person in people.AsParallel()
where person.City == "Seattle"
select person;
```
