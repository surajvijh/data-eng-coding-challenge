# Syft Data Engineer Coding Challenge

This exercise consists of developing a simple tool to compute the continuity of work for the workers on the platform.


## Data Format

In `worker_activity.csv`, you will find data structured as below (here ordered by Worker for convenience):

```
Worker, Employer, Role, Date
1435, 234, 86,  2020-01-01
1435, 234, 86,  2020-01-04
1435, 234, 86,  2020-01-08
135,  45,  696, 2020-01-25
135,  45,  95,  2020-01-27
135,  45,  95,  2020-01-29
456,  78,  576, 2020-02-02
456,  78,  576, 2020-11-29
```


## Continuity of Work

We want to generate a report describing the continuity of work for each user *as of 2020-12-01*. 
We increment continuity for each day worked, and the counter is reset when one of the rules below apply:

* A worker had no activity for more than 6 days.
* A worker stayed active but switched to a different employer.
* A worker stayed active but switched to a different role.

In the dataset above, this gives:

* Worker `1435` worked three different days between January 1st and January 8, and never switched role nor employer. So continuity=3
* Worker `135` appears three times, but switched role after the first occurrence; thus we only count the last two positions, therefore continuity=2.
* Worker `456` worked a first time in February 2020, then paused for more than 6 weeks, then worked again in November 2020; so continuity=1.


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
It's recommended to spend approximately 1 hour on this challenge. However, you are free to elaborate as much as you want to show us your ability to deliver great software!
