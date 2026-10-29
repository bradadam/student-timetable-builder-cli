# Student Course Registration & Timetable Builder CLI

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?logo=python&logoColor=white)
![Interface](https://img.shields.io/badge/Interface-CLI-4EAA25?logo=gnu-bash&logoColor=white)
![Dependencies](https://img.shields.io/badge/Dependencies-None%20(Standard%20Library)-brightgreen)
![Status](https://img.shields.io/badge/Status-Complete-blue)

A lightweight, interactive command-line application built in **Python** that simulates a university student course registration portal. The system enforces academic rules—including a **21-credit semester cap**, **duplicate enrollment prevention**, and **real-time timetable clash detection**—before compiling a structured weekly class schedule.

---

## Key Features

* **Multi-Stage Enrollment Validation:** Every course addition passes through a 4-step verification pipeline:
  1. **Student Session Check:** Ensures an active student profile is registered prior to enrollment.
  2. **Catalog Lookup:** Case-insensitive course code matching against the available curriculum database.
  3. **Credit Limit Enforcement (`check_credit_limit`):** Prevents students from exceeding the maximum **21-credit** university workload per semester.
  4. **Schedule Clash Detection (`detect_clash`):** Rejects courses that overlap in day and time with already-registered classes.
* **Dynamic Add & Drop Workflow:** Automatically recalculates total active credits whenever courses are added or dropped.
* **Automated Timetable Generator:** Renders a clean, chronological weekly schedule organized by day and time slot.

---

## Preloaded Curriculum Catalog

The system includes a sample **Bachelor of Artificial Intelligence (`SAIA`)** course database for testing:

| Course Code | Course Name | Credits | Day | Time Slot |
| :--- | :--- | :---: | :---: | :---: |
| `SAIA1113` | Programming Fundamentals | 3 | Monday | 08:00 - 10:00 |
| `SAIA1123` | Discrete Structure for AI | 3 | Monday | 10:00 - 12:00 |
| `SAIA1133` | Probability & Statistical Data Analysis | 3 | Tuesday | 08:00 - 10:00 |
| `SAIA2113` | Machine Learning | 3 | Tuesday | 08:00 - 10:00 *(Clash Test)* |
| `SAIA2124` | Deep Learning & Neural Networks | 4 | Wednesday | 14:00 - 17:00 |
| `SAIA2133` | Computer Vision | 3 | Thursday | 10:00 - 12:00 |
| `SAIA3114` | Reinforcement Learning | 4 | Thursday | 14:00 - 17:00 |
| `SAIA3123` | Natural Language Processing | 3 | Friday | 09:00 - 11:00 |
| `ULRS1012` | Philosophy and Current Issues | 2 | Friday | 11:00 - 13:00 |

---

## Interactive CLI Preview

```text
=======================================================
    STUDENT COURSE REGISTRATION & TIMETABLE BUILDER
=======================================================
1. Register New Student
2. Add Course
3. Drop Course
4. View Registered Courses
5. Generate Timetable
6. Exit
-------------------------------------------------------
Select an option (1-6): 2

Enter course code to add (e.g. SAIA1113): SAIA1113
Course SAIA1113 (Programming Fundamentals) added successfully!
Total credits: 3/21

-------------------------------------------------------
Select an option (1-6): 2

Enter course code to add (e.g. SAIA1113): SAIA2113
Error: Schedule clash detected with SAIA1133 on Tuesday (08:00 - 10:00)!

-------------------------------------------------------
Select an option (1-6): 5

=======================================================
           WEEKLY TIMETABLE — BRADLEY (A24AI0001)
=======================================================
Day         Time            Code       Course Name
-------------------------------------------------------
Monday      08:00 - 10:00   SAIA1113   Programming Fundamentals
Wednesday   14:00 - 17:00   SAIA2124   Deep Learning & Neural Networks
=======================================================
Total Registered Credits: 7/21
```

---

## Architecture & Module Breakdown

| Function | Responsibility |
| :--- | :--- |
| `display_menu()` | Renders the interactive CLI loop header and navigation options. |
| `register_student()` | Initializes or resets student profile state (`name`, `matric_no`, `registered_courses`, `total_credits`). |
| `check_credit_limit()` | Validates whether `current_credits + new_course_credit <= 21`. |
| `detect_clash()` | Checks for duplicate enrollments and overlapping `day` + `time` slots. |
| `add_course()` | Orchestrates input sanitization, catalog lookup, credit check, and clash check. |
| `drop_course()` | Removes a course by code and decrements the student's active credit count. |
| `view_registered_courses()` | Displays currently enrolled subjects and credit progress. |
| `generate_timetable()` | Sorts and formats registered courses into a weekly timetable view. |

---

## Getting Started

### 1. Clone the repository
```bash
git clone [https://github.com/YOUR-USERNAME/student-timetable-builder-cli.git](https://github.com/YOUR-USERNAME/student-timetable-builder-cli.git)
cd student-timetable-builder-cli
```

### 2. Run the application
No external packages are required. Run directly with Python 3:
```bash
python main.py
```
