# AI-Based Study Planner – Rational Agent

## 📌 Project Overview

The **AI-Based Study Planner** is a Python-based Rational Agent that generates a personalized weekly study timetable based on the student's subjects, deadlines, difficulty levels, priorities, and available study hours.

The agent uses a **utility-based decision-making approach** to determine which subjects should receive higher study priority.

## 🎯 Objective

The main objective of this project is:

> **To maximize coverage of urgent and high-priority topics before their deadlines.**

The system helps students organize their study time by automatically prioritizing subjects according to their importance, difficulty, and deadline urgency.

## 🧠 Rational Agent

This project demonstrates the concept of a **Rational Agent in Artificial Intelligence**.

The agent observes the available subject information and selects study tasks that maximize the calculated utility.

### Agent Inputs

* Subject name
* Deadline
* Difficulty level
* Priority/weight
* Available study hours per day

### Agent Output

* Utility score for each subject
* Priority order of subjects
* 7-day study timetable
* Study hours allocated to each subject
* Reasoning behind the agent's decisions

## ⚙️ Utility Function

The agent calculates the utility score using:

```text
Utility = (Priority × Difficulty × 10) / Remaining Days
```

Where:

* **Priority** → Importance of the subject
* **Difficulty** → Difficulty level from 1 to 5
* **Remaining Days** → Number of days until the deadline
* **10** → Scaling factor used to make the utility score easier to interpret

A higher utility score indicates greater urgency and importance.

## 🔄 Methodology

The system follows these steps:

1. Get the number of subjects from the user.
2. Get the available study hours per day.
3. Collect subject details.
4. Calculate the remaining days until each deadline.
5. Calculate the utility score.
6. Sort subjects according to utility.
7. Allocate study hours based on utility.
8. Generate a 7-day timetable.
9. Display the timetable.
10. Explain why the agent's decision is rational.

## 📊 Study Time Allocation

The agent allocates study time based on the utility score:

| Utility Score |      Study Time |
| ------------- | --------------: |
| 10 or above   |   Up to 2 hours |
| 5 – 9.99      | Up to 1.5 hours |
| Below 5       |    Up to 1 hour |

The allocation is also limited by the student's available study hours per day.

## 🛠️ Technologies Used

* **Python**
* `datetime`
* `timedelta`
* Object-Oriented Programming
* Utility-Based Rational Agent
* Sorting and Decision-Making

## 📂 Project Structure

```text
AI-Study-Planner/
│
├── study_planner.py
├── README.md
└── .gitignore
```

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone <YOUR-GITHUB-REPOSITORY-URL>
```

### 2. Open the project folder

```bash
cd AI-Study-Planner
```

### 3. Run the Python program

```bash
python study_planner.py
```

### 4. Enter the required details

The program asks for:

```text
Enter the number of subjects:
Enter available study hours per day:
Subject name:
Deadline (YYYY-MM-DD):
Difficulty (1 = Easy, 5 = Very Hard):
Priority/Weight (1 = Low, 5 = Very High):
```

## 💻 Sample Input

```text
Enter the number of subjects: 3
Enter available study hours per day: 4

Subject 1
Subject name: Artificial Intelligence
Deadline: 2026-09-25
Difficulty: 5
Priority/Weight: 5

Subject 2
Subject name: Python
Deadline: 2026-09-28
Difficulty: 3
Priority/Weight: 4

Subject 3
Subject name: Database
Deadline: 2026-10-02
Difficulty: 2
Priority/Weight: 3
```

## 📋 Sample Output

```text
============================================================
          AI-BASED WEEKLY STUDY PLANNER
============================================================

Objective: Maximize coverage of urgent and high-priority
topics before deadlines

Available Study Hours Per Day: 4.0

------------------------------------------------------------
Thursday, 17-09-2026
------------------------------------------------------------
📚 Artificial Intelligence | 2 hour(s) | Utility Score: ...
📚 Python | 1.5 hour(s) | Utility Score: ...
📚 Database | 0.5 hour(s) | Utility Score: ...

------------------------------------------------------------
Friday, 18-09-2026
------------------------------------------------------------
📚 Artificial Intelligence | 2 hour(s) | Utility Score: ...
📚 Python | 1.5 hour(s) | Utility Score: ...
📚 Database | 0.5 hour(s) | Utility Score: ...
```

The exact utility scores and dates will change depending on the current date and user inputs.

## 🤖 Why Is the Agent Rational?

The agent is considered rational because it uses available information to make study-planning decisions based on utility.

It considers:

* **Priority** – important subjects receive more attention.
* **Difficulty** – difficult subjects require more preparation.
* **Deadline** – subjects with closer deadlines become more urgent.

The agent then prioritizes subjects with higher utility scores and generates a timetable within the available daily study hours.

## ✅ Advantages

* Automatically prioritizes subjects.
* Considers deadline urgency.
* Considers subject difficulty.
* Considers subject importance.
* Generates a weekly timetable.
* Demonstrates utility-based rational decision-making.
* Simple and easy to use.

## 🚀 Future Enhancements

The project can be extended with:

* Graphical user interface
* Streamlit web application
* Automatic timetable optimization
* Break and revision scheduling
* Progress tracking
* Exam timetable integration
* Machine learning-based study recommendations
* Notifications and reminders
* Database storage for student schedules

## 📚 AI Concepts Demonstrated

This project demonstrates:

* Rational Agents
* Utility-Based Agents
* Agent Decision Making
* State and Environment
* Goal-Oriented Planning
* Priority-Based Scheduling

## 👩‍💻 Author

**Anslin Jeni**

AI & Machine Learning Student

## 📄 License

This project is created for **educational and academic purposes**.

