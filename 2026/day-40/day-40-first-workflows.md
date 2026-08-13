\# Day 40 – Your First GitHub Actions Workflow



\## Objective



The goal of Day 40 was to create my first GitHub Actions workflow and understand how CI/CD automation runs in the cloud.



I created a public GitHub repository named:



`github-actions-practice`



\---



\# Task 1 – Repository Setup



Created a public GitHub repository:



`github-actions-practice`



Cloned the repository locally and created the required GitHub Actions workflow directory:



```text

.github/workflows/

```



Final project structure:



```text

github-actions-practice/

├── .github/

│   └── workflows/

│       └── hello.yml

└── 2026/

&#x20;   └── day-40/

&#x20;       ├── day-40-first-workflow.md

&#x20;       ├── day-40-green.png

&#x20;       └── day-40-failed.png

```



\---



\# Task 2 – First GitHub Actions Workflow



Created the workflow file:



```text

.github/workflows/hello.yml

```



The workflow is triggered whenever code is pushed to the repository.



\## Initial Workflow



```yaml

name: Hello GitHub Actions



on:

&#x20; push:



jobs:

&#x20; greet:

&#x20;   runs-on: ubuntu-latest



&#x20;   steps:

&#x20;     - name: Checkout code

&#x20;       uses: actions/checkout@v4



&#x20;     - name: Say Hello

&#x20;       run: echo "Hello from GitHub Actions!"

```



The workflow successfully ran on GitHub Actions.



\## First Green Pipeline



!\[First Green GitHub Actions Run](day-40-green.png)



The `greet` job completed successfully.



The workflow printed:



```text

Hello from GitHub Actions!

```



\---



\# Task 3 – Understanding Workflow Anatomy



\## `name:`



Defines the name of the GitHub Actions workflow.



Example:



```yaml

name: Hello GitHub Actions

```



This name is displayed in the GitHub Actions interface.



\---



\## `on:`



Defines when the workflow should run.



Example:



```yaml

on:

&#x20; push:

```



This means the workflow runs whenever code is pushed to the repository.



\---



\## `jobs:`



Defines the jobs that GitHub Actions should execute.



Example:



```yaml

jobs:

&#x20; greet:

```



The workflow contains one job named `greet`.



\---



\## `runs-on:`



Defines the operating system/environment where the job will run.



Example:



```yaml

runs-on: ubuntu-latest

```



The job runs on a GitHub-hosted Ubuntu runner.



\---



\## `steps:`



Contains the individual tasks executed inside a job.



Example:



```yaml

steps:

```



Each step performs a specific action or command.



\---



\## `uses:`



Uses an existing GitHub Action.



Example:



```yaml

uses: actions/checkout@v4

```



`actions/checkout@v4` checks out the repository code onto the GitHub Actions runner.



\---



\## `run:`



Executes a shell command on the GitHub Actions runner.



Example:



```yaml

run: echo "Hello from GitHub Actions!"

```



This prints the message in the workflow logs.



\---



\## `name:` on a Step



Provides a readable name for an individual step.



Example:



```yaml

\- name: Say Hello

```



This makes the workflow logs easier to understand.



\---



\# Task 4 – Adding More Steps



The workflow was updated to perform additional tasks:



1\. Print the current date and time

2\. Print the branch that triggered the workflow

3\. List repository files

4\. Print the runner operating system



\## Final Workflow



```yaml

name: Hello GitHub Actions



on:

&#x20; push:



jobs:

&#x20; greet:

&#x20;   runs-on: ubuntu-latest



&#x20;   steps:

&#x20;     - name: Checkout code

&#x20;       uses: actions/checkout@v4



&#x20;     - name: Say Hello

&#x20;       run: echo "Hello from GitHub Actions!"



&#x20;     - name: Current Date and Time

&#x20;       run: date



&#x20;     - name: Print Branch Name

&#x20;       run: 'echo "Branch: ${{ github.ref\_name }}"'



&#x20;     - name: List Repository Files

&#x20;       run: ls -la



&#x20;     - name: Print Operating System

&#x20;       run: uname -a

```



The workflow successfully executed all steps.



The branch name was obtained using:



```text

${{ github.ref\_name }}

```



The workflow was triggered from the:



```text

main

```



branch.



The workflow also displayed:



\- Current date and time

\- Repository files

\- Runner operating system



\---



\# Task 5 – Break It On Purpose



To understand how a failed pipeline looks, I intentionally added a step that exits with a non-zero status code.



The temporary step was:



```yaml

\- name: Intentional Failure

&#x20; run: exit 1

```



The workflow failed because `exit 1` returns a non-zero exit code.



\## Failed Pipeline



!\[Intentional Failed GitHub Actions Run](day-40-failed.png)



The GitHub Actions log showed:



```text

Error: Process completed with exit code 1.

```



The `Intentional Failure` step was marked with a red ❌.



The previous steps completed successfully, but the job failed when it reached the intentional failure step.



\---



\# Understanding Pipeline Failures



A failed GitHub Actions pipeline appears with a red ❌ status.



To troubleshoot a failure:



1\. Open the GitHub repository.

2\. Go to the \*\*Actions\*\* tab.

3\. Open the failed workflow run.

4\. Open the failed job.

5\. Identify the step marked with ❌.

6\. Expand the step.

7\. Read the error message in the logs.

8\. Fix the problem.

9\. Commit and push the changes.

10\. Verify the next workflow run.



In this task, the failure was intentional and was caused by:



```bash

exit 1

```



After understanding the failure, I removed the failing step and pushed the corrected workflow.



The final workflow completed successfully with a green ✅ status.



\---



\# Final Workflow Verification



The final workflow contains the following steps:



```text

Checkout code

&#x20;     ↓

Say Hello

&#x20;     ↓

Current Date and Time

&#x20;     ↓

Print Branch Name

&#x20;     ↓

List Repository Files

&#x20;     ↓

Print Operating System

&#x20;     ↓

Green ✅

```



\---



\# What I Learned



Through this task I learned:



\- How GitHub Actions workflows are structured

\- Where workflow files are stored

\- How a `push` event triggers a workflow

\- How GitHub-hosted runners work

\- How `actions/checkout` checks out repository code

\- How shell commands are executed using `run:`

\- How GitHub variables such as `github.ref\_name` can be used

\- How to read GitHub Actions workflow logs

\- How a failed pipeline looks

\- How to identify the failed step

\- How to troubleshoot a pipeline failure

\- How to fix a failed workflow

\- How every push can automatically trigger CI/CD automation



\---



\# Final Result



Day 40 successfully completed.



My first GitHub Actions workflow successfully runs in the cloud and performs automated tasks whenever code is pushed to the repository.



\## Repository



`github-actions-practice`



\## Workflow



`.github/workflows/hello.yml`



\## Job



`greet`



\## Runner



`ubuntu-latest`



\## Final Status



\*\*GitHub Actions Pipeline: ✅ Successful\*\*



\---



\# Day 40 Completed



I successfully created, tested, intentionally failed, debugged, fixed, and verified my first GitHub Actions workflow.



\#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham #GitHubActions #DevOps #CICD

