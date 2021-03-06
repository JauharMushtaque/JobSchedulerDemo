# JobSchedulerDemo
Job Scheduler Demo App

•	JobScheduler provides a flexible framework to intelligently accomplish background services.

•	JobScheduler is only available on devices running API 21 and higher.

•	To use the JobScheduler, you need two parts: JobService and JobInfo.

•	JobInfo is a set of conditions that trigger the job to run.

•	JobService implements the job to run under the conditions specified by JobInfo.

•	You only have to implement the onStartJob() and onStopJob() callback methods, which you do in your JobService.

•	The implementation of your job occurs, or is started, in onStartJob().

•	The onStartJob() method returns a boolean value that indicates whether the service needs to process the work in a separate thread.

•	If onStartJob() returns true, you must explicitly call jobFinished(). If onStartJob() returns false, the runtime calls jobFinished() on your behalf.

•	JobService is processed on the main thread, so you should avoid lengthy calculations or I/O.

•	JobScheduler is the manager class responsible for scheduling the task. JobScheduler batches tasks to maximize the efficiency of system resources, which means that you do not have exact control of when tasks are executed.


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

The system calls onStartJob() when the system determines that your task should be run and automatically passes in a JobParameters object, which the system creates with information about your job.If your task contains long-running operations, offload the work onto a separate thread. The onStartJob() method returns a boolean: true if your task has been offloaded to a separate thread (meaning it might not be completed yet) and false if there is no more work to be done. Your app must call jobFinished() explicitly in that thread to indicate that the job is complete.

onStopJob()
If the system determines that your app must stop execution of the job, even before jobFinished() is called, the system calls onStopJob(). This happens if the requirements that you specified when you scheduled the job are no longer met.

