# PERT Estimator Pro

**This application was programmed with the assistance of [Gemini](https://gemini.google.com).**

## What is PERT Estimator Pro?

PERT Estimator Pro is a web-based application designed to help users estimate project and task completion times using the Program Evaluation and Review Technique (PERT). It allows for the creation of projects, addition of tasks with optimistic, most likely, and pessimistic time estimates, and automatically calculates expected completion times and variances. 

Furthermore, the application can calculate the probability of completing the entire project within a user-defined "Desired Completion Time." Project data can be saved locally in the browser, as well as imported and exported as JSON files for backup or sharing.

## What is PERT?

PERT (Program Evaluation and Review Technique) is a project management tool used to schedule, organize, and coordinate tasks within a project. It's particularly useful for projects where time is a major factor and there's uncertainty in task duration.

### PERT Calculation

PERT uses a weighted average of three time estimates for each task to determine its **Expected Time (te)**:

1.  **Optimistic Time (O):** The minimum possible time required to accomplish a task, assuming everything proceeds better than is normally expected.
2.  **Most Likely Time (M):** The best estimate of the time required to accomplish a task, assuming everything proceeds as normal.
3.  **Pessimistic Time (P):** The maximum possible time required to accomplish a task, assuming everything goes wrong (excluding major catastrophes).

The formula for **Expected Time (te)** for a single task is:
$te = (O + 4M + P) / 6$

PERT also helps in understanding the uncertainty or **Variance (V)** for each task, which is calculated as:
$V = ((P - O) / 6)^2$

The sum of all task expected times (∑te) gives the project's total expected completion time. The sum of all task variances (∑V) is used to calculate the project's overall standard deviation.

### Project Completion Probability

To estimate the likelihood of completing the project by a specific **Desired Completion Time (Td)**, a Z-score is calculated:

$Z = (Td - \sum te) / \sqrt{\sum V}$

Where:
* $Td$ = Desired Completion Time
* $\sum te$ = Sum of all task expected times (Project's mean completion time)
* $\sum V$ = Sum of all task variances
* $\sqrt{\sum V}$ = Project Standard Deviation (σ)

The Z-score is then used with a standard normal distribution table (or a CDF function) to find the probability of completing the project on or before the Desired Completion Time.

## How to Use the App

### 1. Starting Up

* When you first open the application, you'll see the start screen with options to create a new project, load an existing one or import a project.
* **Create New Project:** Enter a name for your new project in the "New Project Name" field and click "Create Project".
* **Load Saved Project:** If you have previously saved projects, they will be listed under "Saved Projects."
    * Click anywhere on a project's row or its "Load" button to open it.
    * Click the "Delete" button (trash icon) next to a project to remove it from local storage (confirmation will be asked).
* **Import Project:** Click "Import Project from JSON" to load a project from a `.json` file you previously exported.
* **Clear All Projects:** If you have saved projects, a "Clear All Saved Projects" button will be visible. This will remove all project data from your browser's local storage (confirmation will be asked).

### 2. Managing an Active Project (Task Management View)

Once a project is created or loaded, you'll be in the Task Management view.

* **Project Name:**
    * The current project's name is displayed at the top.
    * Click the pencil icon (<i class="bi bi-pencil-square"></i>) next to the project name to edit it. An input field will appear; enter the new name and click the save (<i class="bi bi-check-lg"></i>) button or cancel (<i class="bi bi-x-lg"></i>).
* **Back to Projects:** Click the "<i class="bi bi-arrow-left-circle"></i> Back to Projects" button to return to the start screen.
* **Export Project:** Click "<i class="bi bi-box-arrow-down"></i> Export Project" to save the current project (including all tasks and the desired completion time) as a JSON file.
* **Desired Completion Time:**
    * Enter the overall time by which you hope to complete the project in the "Desired Completion Time" field. This is used for the probability calculation.
    * This value is saved with your project.

* **Adding Tasks:**
    1.  In the "Add New Task" section, fill in the "Task Name."
    2.  Enter the "Optimistic (O)", "Most Likely (M)", and "Pessimistic (P)" time estimates for the task. These must be non-negative numbers.
    3.  Click "Add Task." The task will appear in the "Task List & Estimates" table below. Its Expected Time (te) and Variance (V) will be calculated automatically.

* **Task List & Estimates Table:**
    * Displays all tasks for the current project with their O, M, P, te, and V values.
    * **Edit Task:** Click the pencil icon (<i class="bi bi-pencil-square"></i>) in a task's row to load its details into the "Add New Task" form (which will change to "Edit Task"). Modify the values and click "Update Task."
    * **Delete Task:** Click the trash icon (<i class="bi bi-trash3-fill"></i>) in a task's row to remove it (confirmation will be asked).

* **Project Totals:**
    * Below the task table, the sum of all O, M, P, Expected Times (∑te), and Variances (∑V) for the entire project is displayed.

* **Project Completion Probability:**
    * This section shows:
        * **Project Standard Deviation (σ):** Calculated as $\sqrt{\sum V}$. Hover over the label for a description.
        * **Z-score:** Calculated based on your "Desired Completion Time" and the project's statistics. Hover over the label for a description.
        * **Likelihood of Completion:** The probability (as a percentage) that the project will be completed by the "Desired Completion Time." The color of the percentage (red/yellow/green) indicates low/medium/high probability.
    * This analysis updates automatically when tasks are changed or when the "Desired Completion Time" is modified.

### 3. Data Persistence

* All project data (project names, tasks, desired completion times) is automatically saved to your browser's Local Storage as you make changes.
* When you revisit the app, your saved projects will be available on the start screen.
* The import/export JSON feature provides an additional way to back up or transfer project data.

---

Happy estimating!

