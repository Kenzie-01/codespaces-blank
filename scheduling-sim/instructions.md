This project is a bit different from other projects you may have experienced.  This is a *simulation* homework.

### Overview: 

Most of this document is a short tutorial designed to refresh your memory on how to use command line flags (options) to control the behavior of a program.  In this case, we'll be using many different command line flags to control different scheduling algorithms and then investigate them. 

After you work through the tutorial, there are questions to answer in the README.md file. You should be familiar with markdown after your previous assignments, but if you need a refresher, you can find a tutorial here: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github
That will show you how to easily format tables, font styles (bold, italics), insert links and images, etc.

### Tutorial:

The program you are given, `scheduler.py`, allows you to see how different schedulers perform
given scheduling metrics such as response time, turnaround time, and total
wait time. Three schedulers are simulated: FIFO (first-in-first-out), SJF (shortest job first), and RR (round robin).

Let's look at a specific example: if you want to compute response,
turnaround, and wait for three jobs using the FIFO policy, you would run this:
```
  python scheduler.py -p FIFO -j 3 -s 100
```

Let's get into specifics:
This specifies the FIFO **p**olicy (the `-p` flag) with three **j**obs (the `-j` flag), and, importantly, a specific
random **s**eed of 100 (the `-s` flag). Play around with the argument for the `-s` flag. Note that when the value is the same, the program gives you the same result.  But if you change the argument, the behavior of the program changes. In other words, if you want to see the exact problem, you have to specify this exact same random seed again. 

Let's run it and see
what happens. This is what you should see:

```
prompt> python scheduler.py -p FIFO -j 3 -s 100
ARG policy FIFO
ARG jobs 3
ARG maxlen 10
ARG seed 100

Here is the job list, with the run time of each job: 
  Job 0 (length = 2)
  Job 1 (length = 5)
  Job 2 (length = 8)

Compute the turnaround time, response time, and wait time for each job.  When you are done, run this program again, with the same arguments, but with -c, which will thus provide you with the answers. You can use -s <somenumber> or your own job list (-l 10,15,20 for example) to generate different problems for yourself.
```

As you can see from this example, three jobs are generated: job 0 of length 2,
job 1 of length 5, and job 2 of length 8. As the program states, you can now
use this to compute some statistics and see if you have a grip on the basic
concepts. *Protip: This is great practice for quiz questions!* 

Once you are done, you can use the same program to "solve" the problem and see
if you did your work **c**orrectly. To do so, use the `-c` flag, so:

```
prompt> python scheduler.py -p FIFO -j 3 -s 100 -c
ARG policy FIFO
ARG jobs 3
ARG maxlen 10
ARG seed 100

Here is the job list, with the run time of each job: 
  Job 0 ( length = 2 )
  Job 1 ( length = 5 )
  Job 2 ( length = 8 )


** Solutions **

Execution trace:
  [ time   0 ] Run job 0 for 2.00 secs ( DONE at 2.00 )
  [ time   2 ] Run job 1 for 5.00 secs ( DONE at 7.00 )
  [ time   7 ] Run job 2 for 8.00 secs ( DONE at 15.00 )

Final statistics:
  Job   0 -- Response: 0.00  Turnaround 2.00  Wait 0.00
  Job   1 -- Response: 2.00  Turnaround 7.00  Wait 2.00
  Job   2 -- Response: 7.00  Turnaround 15.00  Wait 7.00

  Average -- Response: 3.00  Turnaround 8.00  Wait 3.00

```

As you can see from the data, the -c flag shows you what happened. 
1. Job 0 ran
first for 2 seconds
2. Job 1 ran second for 5
3. Job 2 ran for 8
seconds.

Not too hard; it is FIFO, after all! The execution trace shows these
results.

The final statistics are useful too: they compute the "response time" (the
time a job spends waiting after arrival before first running), the "turnaround
time" (the time it took to complete the job since first arrival), and the
total "wait time" (any time spent ready but not running). The stats are shown
per job and then as an average across all jobs. Of course, you should have
computed these things all before running with the `-c` flag!

If you want to try the same type of problem but with different inputs, try
changing the number of jobs or the random seed or both. Different random seeds
basically give you a way to generate an infinite number of different problems
for yourself, and the `-c` flag lets you check your own work. Keep doing this
until you feel like you really understand the concepts.

One other useful flag is `-l` (that's a lower-case L), which lets you specify
a **l**ist of jobs you wish to see scheduled. For example, if you want to find out
how SJF would perform with three jobs of lengths 5, 10, and 15, you can run:

```
prompt> python scheduler.py -p SJF -l 5,10,15
ARG policy SJF
ARG jlist 5,10,15

Here is the job list, with the run time of each job: 
  Job 0 (length = 5.0)
  Job 1 (length = 10.0)
  Job 2 (length = 15.0)
...
```

And then you can use `-c` to solve it again. Note that when you specify the
exact jobs, there is no need to specify a random seed or the number of jobs:
the jobs lengths are taken from your comma-separated list.

Of course, more interesting things happen when you use SJF (shortest-job
first) or even RR (round robin) schedulers. Try them and see!

And you can always run 

```
  prompt> python scheduler.py -h 
```

to get a complete list of flags and options (including options such as setting
the time quantum for the RR scheduler).

  
