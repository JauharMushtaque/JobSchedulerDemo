# JobSchedulerDemo
Job Scheduler Demo App

use the JobScheduler class to schedule the job. To obtain an instance of this class, call getSystemService(JOB_SCHEDULER_SERVICE). Then schedule a job using the schedule() method, passing in the JobInfo object you created with the JobInfo.Builder. schedule() method example mScheduler.schedule(myJobInfo)

you can use the AlarmManager class to trigger events based on the real-time clock, or based on elapsed time since boot.
But in Most tasks, however, do not require an exact time, but should be scheduled based on a combination of system and user requirements in this case We can use JobScheduler.

The JobScheduler class allows you to set the conditions, or parameters, for when to run your task. 

Based on the conditions, JobScheduler calculates the best time to schedule the execution of the job. For example, job parameters can include the persistence of the job across reboots, whether the device is plugged in, or whether the device is idle.

To use JobScheduler, you need to use JobService and JobInfo:
•	A JobInfo object contains the set of conditions that trigger a job to run, uses the builder pattern to set the conditions for the task.
•	Get user input to configure constraints (such as waiting until the device is charging) on the JobService.

JobScheduler is only available on devices running API 21 and higher, and is currently not available in the support library. For backward compatibility, use WorkManager.

Add permissions in subclass of JobService  android:permission="android.permission.BIND_JOB_SERVICE"
In your subclass of JobService, override two methods, onStartJob() and onStopJob().

The system calls onStartJob() and automatically passes in a JobParameters object, which the system creates with information about your job.
If your task contains long-running operations, offload the work onto a separate thread. The onStartJob() method returns a boolean: true if your task has been offloaded to a separate thread (meaning it might not be completed yet) and false if there is no more work to be done.

onStopJob()
If the system determines that your app must stop execution of the job, even before jobFinished() is called, the system calls onStopJob(). This happens if the requirements that you specified when you scheduled the job are no longer met.

