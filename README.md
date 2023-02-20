# HighPeak
# Function to solve the job selection problem
def select_jobs(n, jobs):
    # Sort the jobs based on their end times in non-decreasing order
    jobs.sort(key=lambda x: x[1])

    # Select the jobs
    selected_jobs = []
    prev_end = 0
    total_profit = 0
    for job in jobs:
        if job[0] >= prev_end:
            selected_jobs.append(job)
            total_profit += job[2]
            prev_end = job[1]

    # Compute the number of jobs left and the earnings of other employees
    jobs_left = n - len(selected_jobs)
    other_earnings = sum(job[2] for job in jobs) - total_profit

    # Print the output
    print("The number of tasks and earnings available for others")
    print("Task:", jobs_left)
    print("Earnings:", other_earnings)


# Read the input
n = int(input("Enter the number of Jobs\n"))
jobs = []
for i in range(n):
    start_time = int(input("Enter job start time\n"))
    end_time = int(input("Enter job end time\n"))
    profit = int(input("Enter job profit\n"))
    jobs.append((start_time, end_time, profit))

# Solve the problem
select_jobs(n, jobs)


#TestCase :
      Enter the number of Jobs
3
Enter job start time
800
Enter job end time
1050
Enter job profit
570
Enter job start time
500
Enter job end time
900
Enter job profit
760
Enter job start time
3400
Enter job end time
4500
Enter job profit
670
The number of tasks and earnings available for others
Task: 1
Earnings: 570
