# Day 41 – Triggers & Matrix Builds

## Task 1 – Trigger on Pull Request

Created:

`.github/workflows/pr-check.yml`

### Configuration

- Trigger: `pull_request`
- Target branch: `main`
- Events:
  - `opened`
  - `synchronize`

### Output

The workflow prints:

`PR check running for branch: <branch name>`

### Result

The PR workflow was created successfully and is configured to run when a Pull Request is opened or updated against `main`.

---

## Task 2 – Scheduled Trigger

Added a scheduled trigger to:

`.github/workflows/hello.yml`

### Schedule

Every day at midnight UTC:

`0 0 * * *`

### Cron Question

Cron expression for every Monday at 9 AM UTC:

`0 9 * * 1`

### Cron Breakdown

- `0` = Minute
- `9` = Hour
- `*` = Every day of the month
- `*` = Every month
- `1` = Monday

### Result

The scheduled trigger was added successfully.

---

## Task 3 – Manual Trigger

Created:

`.github/workflows/manual.yml`

### Trigger

`workflow_dispatch`

### Input

The workflow asks for an `environment` value.

Available options:

- `staging`
- `production`

### Output

The selected environment is printed in the workflow logs.

Example:

`Selected environment: staging`

### Result

The workflow can be triggered manually from the GitHub Actions tab using **Run workflow**.

---

## Task 4 – Matrix Builds

Created:

`.github/workflows/matrix.yml`

### Python Versions

The matrix runs the same job with:

- Python 3.10
- Python 3.11
- Python 3.12

### Initial Result

3 Python versions = 3 jobs

Each job installs its Python version and prints the installed version.

### Operating Systems

The matrix was extended with:

- Ubuntu
- Windows

Therefore:

2 Operating Systems × 3 Python Versions = 6 jobs

### Result

The matrix successfully runs jobs across multiple Python versions and operating systems.

---

## Task 5 – Exclude & Fail-Fast

### Exclude

The following combination was excluded:

`Windows + Python 3.10`

Originally:

2 Operating Systems × 3 Python Versions = 6 jobs

After excluding one combination:

6 - 1 = 5 jobs

### Final Matrix Jobs

- Ubuntu + Python 3.10
- Ubuntu + Python 3.11
- Ubuntu + Python 3.12
- Windows + Python 3.11
- Windows + Python 3.12

### Fail-Fast

Configured:

`fail-fast: false`

### Difference

**fail-fast: true**

If one matrix job fails, GitHub Actions cancels the remaining in-progress matrix jobs.

**fail-fast: false**

If one matrix job fails, the other matrix jobs continue running.

This is useful when we want to see the result of every matrix combination.

---

## Screenshots

### Task 1 – Pull Request

Add screenshot of the Pull Request workflow.

### Task 2 – Scheduled Trigger

Add screenshot of the scheduled workflow.

### Task 3 – Manual Trigger

Add screenshot of the manual workflow and selected environment.

### Task 4 – Matrix Build

Add screenshot showing multiple Python versions running.

### Task 5 – Matrix with OS

Add screenshot showing the final matrix jobs.

---

## GitHub Actions Triggers Learned

| Trigger | Purpose |
|---|---|
| `push` | Runs when code is pushed |
| `pull_request` | Runs for Pull Request events |
| `schedule` | Runs automatically using cron |
| `workflow_dispatch` | Runs manually |

---

## Key Learnings

- Learned Pull Request triggers.
- Learned scheduled workflows using cron.
- Learned manual workflow triggers.
- Learned workflow inputs.
- Learned matrix builds.
- Learned how to test multiple Python versions.
- Learned how to test multiple operating systems.
- Learned matrix exclusions.
- Learned `fail-fast: true` and `fail-fast: false`.

---

## Conclusion

Day 41 completed successfully.

I learned how GitHub Actions can be triggered by different events and how matrix builds can test the same workflow across multiple Python versions and operating systems.

Matrix builds make CI/CD pipelines more flexible and powerful by allowing multiple environments to be tested automatically.

---

## Day 41 Checklist

- [x] Task 1 – Pull Request Trigger
- [x] Task 2 – Scheduled Trigger
- [x] Task 3 – Manual Trigger
- [x] Task 4 – Matrix Builds
- [x] Task 5 – Exclude & Fail-Fast
- [x] Documentation