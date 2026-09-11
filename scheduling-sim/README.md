Collaboration Statement (including AI usage):

**Command line flag proficiency:**
1. Give the commands (including flags) which allow you to compute the response time and turnaround time when running three jobs of length 200 with the SJF and FIFO schedulers.

   * SJF - python scheduler.py -p SJF -j 3 -l 200,200,200 -c
   * FIFO - python scheduler.py -p FIFO -j 3 -l 200,200,200 -c

2. Now do the same but with jobs of different lengths: 100, 200, and 300.

   * SJF - python scheduler.py -p SJF -j 3 -l 100,200,300 -c
   * FIFO - python scheduler.py -p FIFO -j 3 -l 100,200,300 -c

3. Now do the same, but also with the RR scheduler and a time-slice of 1.

   * RR - python scheduler.py -p RR -j 3 -q 1 -c

**Thought questions:**

For each of the following, be sure to justify your answer with program runs, examples, and/or diagrams. (*Note: you can upload pictures to your directory and then link them from your README.md document.*)

4. For what types of workloads does SJF deliver the same turnaround times as FIFO? Justify your answer with program runs and examples.

   * SJF and FIFO deliver the same turnaround times when both have the workload of 1. 

   ![alt text](<Screenshot 2026-09-11 182807.png>)

   ![alt text](<Screenshot 2026-09-11 182738.png>)

5. For what types of workloads and quantum lengths does SJF deliver the same response times as RR?

   * For SJF and RR to have the same response times SJF need to have the workload of 3 and the quantum length of 4 while RR has the workload of 3 and quantum length of 6.

   ![alt text](<Screenshot 2026-09-11 185112-1.png>)

   ![alt text](<Screenshot 2026-09-11 185137.png>)

6. What happens to response time with SJF as job lengths increase?
Can you use the simulator to demonstrate the trend?

   * The response time for SJF increases everytime the job length increases.

   ![alt text](<Screenshot 2026-09-11 185829.png>)

   ![alt text](<Screenshot 2026-09-11 185856.png>)

   ![alt text](<Screenshot 2026-09-11 185921.png>)

7. What happens to response time with RR as quantum lengths increase? What is the worst-case response time, given N jobs?

   * 

   * 

