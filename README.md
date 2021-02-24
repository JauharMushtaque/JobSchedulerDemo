# JobSchedulerDemo
Job Scheduler Demo App

you can use the AlarmManager class to trigger events based on the real-time clock, or based on elapsed time since boot.
Most tasks, however, do not require an exact time, but should be scheduled based on a combination of system and user requirements.

The JobScheduler class allows you to set the conditions, or parameters, for when to run your task. 

Based on the conditions, JobScheduler calculates the best time to schedule the execution of the job. For example, job parameters can include the persistence of the job across reboots, whether the device is plugged in, or whether the device is idle.
