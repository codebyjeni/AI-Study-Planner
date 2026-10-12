# 🎓 AI-Based Study Planner – Rational Agent

## 📌 Project Overview

The **AI-Based Study Planner – Rational Agent** is an intelligent study scheduling system developed as an extension of the IA1 Study Planner into an IA2 final project.

The system generates a study timetable based on subject difficulty, importance, deadlines, required study hours, and prerequisite relationships. It applies **Constraint Satisfaction Problem (CSP)** techniques and knowledge-based reasoning to create a feasible study schedule.

The planner also estimates the likelihood of completing each subject before its deadline and supports timetable replanning when a study session is missed.

## 🎯 Objectives

* Generate an intelligent study timetable using CSP techniques.
* Prioritize subjects based on difficulty, importance, and deadlines.
* Schedule prerequisite subjects before dependent subjects.
* Apply backtracking, Minimum Remaining Values (MRV), and Least Constraining Value (LCV).
* Use forward checking and AC-3-style arc consistency to reduce invalid scheduling choices.
* Apply forward chaining to derive knowledge-based facts.
* Estimate the likelihood of completing subjects before their deadlines.
* Support adaptive replanning after missed study sessions.
* Provide transparent explanations and responsible AI recommendations.

## ✨ Features

### 1. Intelligent Study Scheduling

The system generates a timetable using the following inputs:

* Subject name
* Deadline
* Difficulty level (1–5)
* Importance or weight (1–5)
* Required study hours
* Prerequisite subjects
* Available study sessions per day

### 2. Constraint Satisfaction Problem (CSP)

The scheduling problem is represented using:

| CSP Component          | Description                                                                                                   |
| ---------------------- | ------------------------------------------------------------------------------------------------------------- |
| Variables              | Individual study-hour sessions                                                                                |
| Domains                | Available day and session combinations                                                                        |
| Constraints            | Unique session slots, deadlines, prerequisite ordering, and subject-spacing rules                             |
| Backtracking           | Searches for a valid timetable                                                                                |
| MRV                    | Selects the variable with the fewest legal values                                                             |
| LCV                    | Prefers values intended to restrict other variables less                                                      |
| Forward Checking       | Removes unavailable slots after an assignment                                                                 |
| AC-3-style Propagation | Removes conflicting values from domains, with the current implementation primarily handling singleton domains |

### 3. Knowledge-Based Reasoning

The planner uses a simple rule-based knowledge system to identify:

* Subjects whose required study hours are complete.
* Subjects with no prerequisites.
* Subjects whose prerequisites have been completed.

It displays an inference trace to explain how facts are derived.

### 4. Subject Priority Calculation

The priority score is calculated using:

**Priority = (Difficulty × Importance) / Days Left**

Higher-priority subjects receive greater consideration during scheduling.

### 5. Completion-Likelihood Estimation

The system estimates the likelihood of completing each subject before its deadline using:

* Remaining study hours
* Available study slots
* Subject difficulty
* Calculated priority

The resulting percentage is a **heuristic estimate, not a statistically calibrated probability**.

### 6. Baseline vs. Improved Search

The project compares two scheduling approaches:

* Plain backtracking
* Backtracking with MRV, LCV, forward checking, and AC-3-style propagation

It reports search nodes, backtracks, and arc-consistency revisions.

### 7. Adaptive Replanning

The system includes a basic replanning demonstration for missed study sessions. It generates a revised timetable for remaining subjects.

**Current limitation:** The implementation regenerates the timetable rather than preserving all completed sessions and existing future assignments. Therefore, it demonstrates basic replanning but not complete progress-preserving adaptive scheduling.

### 8. Responsible AI

The planner provides explanations for its recommendations and highlights the importance of:

* Accurate input data
* Human review of scheduling recommendations
* Fair distribution of study workload
* Protecting students' private information
* Understanding the limitations of heuristic estimates

## 🛠️ Technologies Used

* **Programming Language:** Python
* **Concepts:** Artificial Intelligence, Rational Agents, Constraint Satisfaction Problems, Knowledge-Based Systems
* **Algorithms:** Backtracking, MRV, LCV, Forward Checking, AC-3-style Arc Consistency, Forward Chaining
* **Data Structures:** Lists, Dictionaries, Sets, Tuples
* **Modules:** `argparse`, `copy`, `json`, `dataclasses`, `datetime`, `typing`

The current implementation uses Python's standard library and does not require external packages.

## 📂 Project Structure

```text
AI-Study-Planner/
│
├── src/
│   └── study_planner.py
│
├── README.md
└── study_outcomes.json  (optional, if added in a future version)
```

**Note:** The current code imports `json`, but it does not yet save study outcomes to `study_outcomes.json`.

## ⚙️ Installation and Setup

### Step 1: Install Python

Install Python 3.10 or a compatible newer version.

Check the installation:

```bash
python --version
```

### Step 2: Clone the Repository

```bash
git clone https://github.com/codebyjeni/AI-Study-Planner.git
```

### Step 3: Open the Project Folder

```bash
cd AI-Study-Planner
```

### Step 4: Run the Application

Run the interactive study planner:

```bash
python src/study_planner.py
```

Run the planner with sample data:

```bash
python src/study_planner.py --demo
```

## ▶️ How to Use

1. Run the Python program.
2. Enter the number of subjects.
3. Enter each subject's name and deadline.
4. Provide difficulty and importance ratings.
5. Enter the required study hours.
6. Specify prerequisite subjects, if applicable.
7. Enter the number of study sessions available per day.
8. Review the generated timetable.
9. Examine the knowledge-based inference trace.
10. Review completion-likelihood estimates.
11. Compare baseline and improved search statistics.
12. Review the missed-session replanning demonstration.

For the demo mode, the program automatically uses predefined sample subjects.

## 📊 Sample Output

The following is an illustrative example of the output format. Actual results depend on the current date, input values, constraints, and search order.

```text
=== AI-Based Study Planner – Rational Agent (IA2) ===

=== CSP TIMETABLE (MRV + LCV + propagation) ===

Monday:
  Session 1: Mathematics (priority 5.0)
  Session 3: Python (priority 2.5)

Tuesday:
  Session 1: AI Basics (priority 2.0)

=== KNOWLEDGE BASE / FORWARD-CHAINING TRACE ===

FACT/RULE: Python has no prerequisites.

=== UNCERTAINTY / COMPLETION-LIKELIHOOD ESTIMATES ===

Python: 85.0%
  Explanation: Remaining hours and available slots influence the estimate.

=== BASELINE VS IMPROVED SEARCH ===

Plain backtracking: success
MRV + LCV + forward checking + AC-3: success

=== ADAPTIVE REPLANNING DEMO ===

A revised timetable was generated.

=== RESPONSIBLE AI NOTE ===

Review recommendations yourself; the score may reflect inaccurate inputs.
Avoid entering private student identifiers or sensitive personal information.
```

*The values above are examples only and are not guaranteed to match the program's actual output.*

## 🧠 AI Concepts Demonstrated

| AI Concept               | Application                                                    |
| ------------------------ | -------------------------------------------------------------- |
| Rational Agent           | Uses input information to make scheduling decisions            |
| CSP                      | Represents study sessions, domains, and scheduling constraints |
| Backtracking             | Searches for a valid assignment                                |
| MRV                      | Selects a variable with fewer legal options                    |
| LCV                      | Attempts to choose less restrictive values                     |
| Forward Checking         | Removes conflicting domain values after assignments            |
| Arc Consistency          | Applies AC-3-style domain reduction                            |
| Knowledge Representation | Stores subject and prerequisite relationships                  |
| Forward Chaining         | Derives facts using predefined rules                           |
| Uncertainty Estimation   | Calculates heuristic completion-likelihood scores              |
| Adaptive Planning        | Demonstrates timetable regeneration after a missed session     |
| Responsible AI           | Explains recommendations and their limitations                 |

## ⚠️ Limitations

* The timetable covers a configurable number of study days.
* Subjects with deadlines outside the planning horizon may not receive a complete schedule.
* The current AC-3 implementation is simplified and does not implement full general binary arc consistency.
* The completion-likelihood percentage is heuristic rather than empirically validated.
* Replanning regenerates a schedule and does not preserve all previous assignments.
* The current version does not persist study outcomes to a JSON file.
* The system relies on user-provided information and does not independently verify deadlines or completed hours.

## 🚀 Future Enhancements

* Implement full AC-3 with explicit binary constraint relations.
* Preserve completed sessions and unaffected future assignments during replanning.
* Store study progress and outcomes in JSON or a database.
* Add a graphical user interface or web dashboard.
* Introduce automatic progress tracking and missed-session notifications.
* Improve workload balancing and fairness analysis.
* Evaluate completion estimates using real study data.
* Generate visual timetable charts and progress reports.

## 🎓 Conclusion

The AI-Based Study Planner demonstrates how artificial intelligence techniques can be applied to academic scheduling. By combining CSP-based timetable generation, heuristic search, prerequisite reasoning, completion-likelihood estimation, and basic adaptive replanning, the project provides a foundation for an intelligent and explainable study planning system.

The project also highlights the importance of responsible AI through transparent recommendations, human oversight, and privacy awareness.

## 👩‍💻 Author

**Anslin Jeni**

GitHub: [codebyjeni](https://github.com/codebyjeni)

## 📄 License

This project is intended for academic and educational purposes. A specific open-source license can be added if the project is intended for public reuse and distribution.
