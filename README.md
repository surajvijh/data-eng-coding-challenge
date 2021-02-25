# Syft Data Engineer Coding Exercise

This exercise consists of developing a simple tool to identify workers with a X-week continuity of work.

## Data Format

In `worker_activity.csv`, you will find data:

```
WorkerID, Platform, Employer, Role, Date
1435, 12, 234, 86,  2021-01-01 12:00:00
1435, 12, 234, 86,  2021-01-04 12:00:00
456,  53, 78,  576, 2021-01-02 12:00:00
1435, 12, 234, 86,  2021-01-08 12:00:00
135,  6,  45,  696, 2021-01-03 12:00:00
```

## Continuity of Work

We want to generate a report listing all the users who don't match the following rules as of 2021-03-01:

* They have no activity on any platform for more than 6 weeks (42 days, inclusive).
* They stayed on a platform but they switched to a different employer.
* They stayed on a platform but they switched to a different role.


## Results

We expect a `results.csv` file following this format:

```
WorkerID, Days_Continuity
1435, 2
456,  0
135,  1
```

## Bonus Points

Implement your application in a stream-oriented fashion, or document how you would implement this in addition to your batch-oriented implementation.



## Submission

Please write your application in either Python, Java, Scala or Kotlin, with a runnable shell script named `run-app.sh` to launch your application.
Please add the resulting CSV file as well.
Submit all the expected files in a tarball named as follows: `syft-dataeng-<firstname>-<lastname>.tar.gz`.
