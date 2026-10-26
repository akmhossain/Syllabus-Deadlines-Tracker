# Automation Engineeing: Practicum Proposal

## Student Information
- **Name: AKM Hossain**  
- **Instructor: Prof. Washburn**  
- **Date: 12/2026**  

---

## 1. Project Title
> Provide a concise and descriptive title for your automation project.

Tracker for Syllabus Deadlines

---

## 2. Overview / Abstract
> Write a brief (1–2 paragraph) summary of the task you plan to automate.  
I plan to automate the task of keeping track of deadlines throughout all classes by parsing syllabi for all courses at once. There are few professors that might not remind students of any important deadlines or dates. I like to be very organized and aware of my deadlines, so currently I go through each syllabus manually and write down deadlines and test dates. Its a process that takes ~10-15 minutes that I do at the start of every semester. Sometimes I also have to go tweak my calendar because professors decide to change dates because of special circumstances. So, I think it would be useful to automate the process of keeping track of all deadlines by just parsing an uploaded syllabi.


> Include the purpose of the task and why automation is beneficial.

My final application aims to reduce the headache of opening multiple syllabi and keeping track of all the dates. I want to automate the process so the user can get a peace of mind by knowing all their deadlines. The app will also feature the ability to download an .ics file to add to their calendar and enter additonal (reccurring) dates.

---

## 3. Task Description
### 3.1 Manual Process Description
> Describe the task as it is currently performed manually.

- What are the steps?
  - Download and view each syllabus. Look throughout the syllabus for any important dates and record them in your calendar/notes.
- Who performs them?
  - Any student with syllabi they need to keep track of.
- How frequently is the task performed?
  - Every semester or when deadlines are changed.

### 3.2 Problem Statement
> What inefficiencies, challenges, or limitations exist in the current process?

In the current process, it can be tiresome to identify all deadlines, and sometimes the user may miss a date from the syllabus.

### 3.3 Automation Goal
> Clearly define what successful automation looks like.

- What will be improved? (speed, accuracy, scalability, etc.)
  - Speed and scalability will all be increased. Depending on the implementation, parsing all resumes will be faster than just reading one by one, and the app can handle one or multiple resumes at once.

---

## 4. Inputs to the Task
> Describe all inputs required for the task.

### 4.1 Input Sources
- (e.g., files, user input, web APIs, sensors, emails, etc.)
  - The task will require at least one PDF from the user and accept custom user input for additional assignments/dates not mentioned in the PDF.

### 4.2 Input Formats
- (e.g., CSV, JSON, HTML forms, plain text, images)
  - PDF file, plain text

### 4.3 Input Frequency
- One-time, periodic, event-driven, continuous, etc.
  - One-time, event-driven

---

## 5. Outputs and End States
> Describe the expected results of the automated process.

`streamlit_calendar` with months that have an assignment or deadline. ics file for easy upload to other calendar websites/apps.

### 5.1 Outputs
- (e.g., reports, database updates, notifications, API calls)
  - `streamlit_calendar` object, ICS file

### 5.2 Output Formats
- (e.g., PDF, CSV, JSON, email, SMS)
  - .ics, `streamlit_calendar`

### 5.3 End State Conditions
> What conditions indicate the task has completed successfully?

All relevant dates are parsed with accuracy and a `streamlit_calendar` is generated properly showing it clearly. User also has the option to download an ICS file with the relevant information. When the user enters custom input, it is also reflected in the calendar and ICS file.

---

## 6. Data Transformations
> Describe how data is processed and transformed throughout the task.

### 6.1 Transformation Steps
- Input cleaning
- Parsing / extraction
- Filtering / validation
- Aggregation or computation
- Formatting

### 6.2 Transformation Examples
> Provide at least one concrete example:
- Input(pdf) → Transformation(extract dates) → Output(ics)

---

## 7. Proposed Automation Approach
> Explain how you plan to automate the task.

### 7.1 Techniques
- PDF scraping, scheduling

### 7.2 Tools and Technologies
- Please see section `11. Tech Stack` below.

### 7.3 System Architecture (Optional)
> Describe how components interact (you may include a diagram if desired).

Please see `architecture.mmd` for full system architecture.

---

## 8. Pseudocode for Automated Task
> High-level pseudocode that outlines the logic of your automation.

```
syllabi = ask user to upload one or more PDF files
events = an empty list

for each syllabus in syllabi:
    identify the course
    read the syllabus text and tables
    find assignments, quizzes, exams, projects, and labs

    for each item found:
        identify its due date
        if the date is clear:
            mark the item as verified
        else:
            mark the item for user review
        add the item to events

ask user if they want to add a recurring task
if the user provides one:
    create an event for each occurrence
    add the events to events

show all events in a review table
let the user correct or confirm event details
show the confirmed events on the selected month's calendar
create an ICS calendar file from the confirmed events
let the user download the ICS file
```

---

## 9. Testing and Validation Plan
> How will you verify that your automation works correctly?

### Test Cases
- Upload one or more valid syllabi and verify that events are extracted and assigned to the correct courses.
- Test ambiguous, relative, or missing dates and verify that those events are flagged for user review.
- Test an invalid PDF or a syllabus with no recognizable events and verify that the app reports the issue and allows the user to continue.
- Add a recurring task, edit or confirm events, and verify that the calendar and downloaded ICS file reflect the confirmed details.

### Expected vs. Actual Results
For each test, record the input, expected result, actual result, and pass/fail status. The test passes when extracted events match the syllabus or user input, unclear dates are flagged for review, recurring events follow the user input, and calendar and ICS outputs match the confirmed event list.

### Error Handling Strategies
- If no file is uploaded, prompt the user to upload at least one syllabus before processing or ask them to enter atleast one event.
- If a file cannot be read or is not a valid PDF, identify the affected file, explain the issue, and let the user retry without losing previously processed syllabi.
- If a date is ambiguous, missing, or unsupported, mark it for user review and do not silently assign a confirmed date.
- If no events are found, clearly notify the user and allow them to add events manually or upload another syllabus.
- If recurring-task details are incomplete or invalid, explain what needs correction and ask the user to enter the details again.
- If calendar or ICS generation fails, display an error and let the user retry; do not indicate that the export succeeded.


## 10. References (Optional)
> List any resources, documentation, or tools you plan to use.
- streamlit documentation
- documentation of python libraries: re, pdf, dateutil

## 11. Tech Stack
- **Programming language:** Python
- **User interface:** Streamlit
- **PDF extraction:** pdfplumber
- **Event classification:** Regular expressions (`re`)
- **Date parsing and recurrence:** python-dateutil
- **Data aggregation:** pandas
- **Calendar display:** streamlit-calendar
- **Calendar export:** ics

---

## Instructor Feedback (To be completed by instructor)
- Approval Status:
- Comments:
- Suggested Improvements: