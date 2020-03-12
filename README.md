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

This call of AsParallel requests that the query be paralleli?ed whether
performance is improved or not, with the request that the query be executed
on a maximum of four processors:
```
var result ? from person in people.AsParallel()
 .WithDegreeOfParallelism(4) // Set the maximum of four processors at the same time
 .WithExecutionMode(ParallelExecutionMode.ForceParallelism) //Force Paralelism
  where person.City == "Seattle"
select person
```

A parallel query, may process data in a different order from the input data. If it is important that the order of the original data be preserved, the AsOrdered method can be used to request this from the query:
```
var result ? from person in
 people.AsParallel().AsOrdered()
 where person.City ?? "Seattle"
 select person?
```

