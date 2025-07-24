GEU Timetable Viewer
A clean, modern, and mobile-friendly web application to view the B.Tech CSE timetables for Graphic Era University. This project was created to provide a more accessible and user-friendly alternative to the official timetable PDFs.

This application is built with simple HTML, Tailwind CSS, and vanilla JavaScript, making it lightweight and easy to deploy on static hosting platforms like GitHub Pages.

How to Use
Open the website: Access the live URL where the project is hosted.

Select Semester: Click on either the "3rd Semester" or "5th Semester" button.

Select Section: A list of sections for the chosen semester will appear. Click on your section button.

View Timetable: Your weekly timetable will be displayed.

On desktop, you'll see a full weekly grid.

On mobile, you'll see a tabbed view, with the current day selected by default.

View Class Details: Click on any class to see more details, including the full subject name and faculty.

Live Highlighting: The current day and the ongoing lecture are highlighted automatically for quick reference.

How to Contribute
Contributions are welcome, especially for keeping the timetable data up-to-date! The entire timetable is stored within the index.html file. Here’s how you can update it:

1. Find the Data Source
Open the index.html file and scroll down to the <script> tag at the bottom. You will find a large JavaScript object named fullTimetableData. This is where all the magic happens.

<script>
    // --- DATA ---
    const fullTimetableData = {
        '3': {
            subjectDetails: { /* ... */ },
            timetable: { /* ... */ }
        },
        '5': {
            subjectDetails: { /* ... */ },
            timetable: { /* ... */ }
        }
    };
    // ... rest of the script
</script>

2. Updating Timetable Information
The fullTimetableData object is structured by semester. To edit a timetable, find the correct semester key ('3' for 3rd, '5' for 5th).

Inside each semester object, there are two main parts:

subjectDetails: A mapping of subject codes to their full names and faculty.

timetable: The actual schedule for each section.

a) To Update a Class Schedule:
Navigate to timetable -> [Your Section] -> [Day of the Week]. This will give you an array of class objects for that day.

Each class object has two properties:

time: The time slot (e.g., "9:00 - 9:55").

s: The subject code (e.g., "TCS-503").

r: The room number (e.g., "LT-7").

Example: To change the first class for Section A on Monday in the 5th semester, you would edit this line:

// Before
"A": { "Monday": [{ time: "9:00 - 9:55", s: "TCS-503", r: "LT-7" }, /*...*/] }

// After (e.g., changing the subject to TCS-501)
"A": { "Monday": [{ time: "9:00 - 9:55", s: "TCS-501", r: "LT-7" }, /*...*/] }

b) To Update Subject Details (Name/Faculty):
Navigate to subjectDetails. Here you can add or modify subject information.

Example: To update the faculty for TCS-501 for Section A:

// Before
'TCS-501': { name: 'System Software', faculty: { A: 'Old Faculty Name', /*...*/ } },

// After
'TCS-501': { name: 'System Software', faculty: { A: 'New Faculty Name', /*...*/ } },

3. Adding a New Section or Semester
To add a new section (e.g., "I" to 5th Sem): Simply add a new key "I" inside the timetable object for the 5th semester and provide its weekly schedule.

To add a new semester (e.g., "1st Sem"): Add a new key '1' to the main fullTimetableData object, copying the structure of the '3' or '5' semester objects.
