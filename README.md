# Syft Data Engineer Coding Exercise

This exercise consists of developing a simple tool to compute the continuity of work for the workers on the platform.


## Data Format

In `worker_activity.csv`, you will find data structured as below (here ordered by Worker for convenience):

```
Worker, Platform, Employer, Role, Date
1435, 12, 234, 86,  2021-01-01
1435, 12, 234, 86,  2021-01-04
1435, 12, 234, 86,  2021-01-08
135,  6,  45,  696, 2021-01-25
135,  6,  45,  95,  2021-01-27
135,  6,  45,  95,  2021-01-29
456,  53, 78,  576, 2020-11-02
456,  53, 78,  576, 2021-01-29
```


## Continuity of Work

We want to generate a report describing the continuity of work for each user *as of 2021-02-01*. 
We increment continuity for each day worked, and is reset when one of the rules below apply:

* They have no activity on any platform for more than 6 weeks (42 days, inclusive).
* There's activity but they switched to a different platform.
* They stayed on a platform but they switched to a different employer.
* They stayed on a platform but they switched to a different role.

In the dataset above, this gives:

* Worker `1435` worked three different days between January 1st and January 8, only used platform 12, and never switch role nor employer. So continuity=3
* Worker `135` appears three times, but switched role after the first occurrence; thus we only count the last two positions, therefore continuity=2.
* Worker `456` worked a first time in October 2020, then paused for more than 6 weeks, then worked again in January 2021; so continuity=1.


## Results

We expect a `results.csv` file following this format, ordered by Continuity (descending order).
The field `Continuity` is expressed in days.

```
WorkerID, Continuity
1435, 3
135,  2
456,  1
```


## Bonus Points

Implement your application in a stream-oriented fashion, or document how you would implement this in addition to your batch-oriented implementation.


## Open questions

As part of your submission, please answer the following questions in a simple text file.

1. What is the complexity of your algorithm?
2. If you were to review someone else's code, what would you pay attention to?
3. We provided a CSV file for conveniency, but in a production environment, what format or database would you recommend instead for this use-case (and why)?
4. Is there anything else you would implement differently for a large-scale application in production?


## Submission

Please write your application in either Python, Java, Scala or Kotlin, with a runnable shell script named `run-app.sh` to launch your application.
Please add the resulting CSV file as well as all the other materials asked above.
Submit all the expected files in a tarball named as follows: `syft-dataeng-<firstname>-<lastname>.tar.gz`.
