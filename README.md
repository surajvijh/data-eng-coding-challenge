# Syft Data Engineer Coding Exercise

This exercise consists of developing a simple tool to identify workers with a X-days continuity of work.

## Data Format

In `worker_activity.csv`, you will find data:

```
WorkerID, Platform, Employer, Role, Date
1435, 12, 234, 86,  2021-01-01 12:00:00
1435, 12, 234, 86,  2021-01-04 12:00:00
1435, 12, 234, 86,  2021-01-08 12:00:00
135,  6,  45,  696, 2021-01-25 12:00:00
135,  6,  45,  95,  2021-01-27 12:00:00
135,  6,  45,  95,  2021-01-29 12:00:00
456,  53, 78,  576, 2020-11-02 12:00:00
456,  53, 78,  576, 2021-02-01 12:00:00
```

## Continuity of Work

We want to generate a report describing the continuity of work for each user as of 2021-02-01. Continuity is defined as follows:

* They have no activity on any platform for more than 6 weeks (42 days, inclusive).
* They stayed on a platform but they switched to a different employer.
* They stayed on a platform but they switched to a different role.

In the dataset above, this gives:

* Worker 1435 worked three different days between January 1st and January 8, only used platform `12`, and never switch role nor employer. So continuity=3
* Worker 135 has been seen three times, but switched role after the first occurrence; thus we only count the last two positions, continuity=2.
* Worker 456 worked a first time more than 6 weeks ago, and then we saw it again on February 1st, so continuity=1.


## Results

We expect a `results.csv` file following this format:

```
WorkerID, Days_Continuity
1435, 7
135,  1
456,  1
```

## Bonus Points

Implement your application in a stream-oriented fashion, or document how you would implement this in addition to your batch-oriented implementation.



## Submission

Please write your application in either Python, Java, Scala or Kotlin, with a runnable shell script named `run-app.sh` to launch your application.
Please add the resulting CSV file as well.
Submit all the expected files in a tarball named as follows: `syft-dataeng-<firstname>-<lastname>.tar.gz`.
