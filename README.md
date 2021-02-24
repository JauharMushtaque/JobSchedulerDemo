# JobSchedulerDemo
Job Scheduler Demo App

you can use the AlarmManager class to trigger events based on the real-time clock, or based on elapsed time since boot.
But in Most tasks, however, do not require an exact time, but should be scheduled based on a combination of system and user requirements in this case We can use JobScheduler.

The JobScheduler class allows you to set the conditions, or parameters, for when to run your task. 

Based on the conditions, JobScheduler calculates the best time to schedule the execution of the job. For example, job parameters can include the persistence of the job across reboots, whether the device is plugged in, or whether the device is idle.

To use JobScheduler, you need to use JobService and JobInfo:
•	A JobInfo object contains the set of conditions that trigger a job to run, uses the builder pattern to set the conditions for the task.
•	Get user input to configure constraints (such as waiting until the device is charging) on the JobService.

JobScheduler is only available on devices running API 21 and higher, and is currently not available in the support library. For backward compatibility, use WorkManager.
