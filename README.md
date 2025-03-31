
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="google-site-verification" content="-BH3PGI1RwCB9FCLOXXV0p-3-21gsnhuZ5iS8LASdgk" />
    <meta name="description" content="A GPA calculator for University of the West Indies students with grade ranges and quality points.">
    <meta name="keywords" content="UWI GPA calculator, University of the West Indies, GPA calculation, student tools">
    <meta name="author" content="Your Name">
    <title></title>
    <style>
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background-color: #f4f7fa;
            margin: 0;
            padding: 20px;
            color: #333;
        }
        .container {
            max-width: 700px;
            margin: 0 auto;
            background-color: #ffffff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .logo {
            display: block;
            margin: 0 auto 20px;
            max-width: 75px;
        }
        h1 {
            text-align: center;
            color: #004080;
            margin-bottom: 20px;
        }
        .course {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            background-color: #f9f9f9;
            padding: 10px;
            border-radius: 5px;
        }
        label {
            width: 80px;
            font-weight: bold;
            color: #555;
        }
        select {
            padding: 8px;
            margin-right: 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
            width: 160px; /* Increased from 120px to show full text */
            background-color: #fff;
        }
        button {
            padding: 10px 20px;
            margin-right: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }
        button.add {
            background-color: #28a745;
            color: white;
        }
        button.add:hover {
            background-color: #218838;
        }
        button.calculate {
            background-color: #004080;
            color: white;
        }
        button.calculate:hover {
            background-color: #003366;
        }
        button.delete {
            padding: 8px 15px;
            background-color: #ffffff;
            color: #000000;
            border: 1px solid #000000;
        }
        button.delete:hover {
            background-color: #e0e0e0;
        }
        .button-group {
            margin-top: 20px;
            text-align: center;
        }
        #result {
            margin-top: 25px;
            text-align: center;
            font-size: 1.2em;
            font-weight: bold;
            color: #004080;
        }
        .grade-table {
            margin-top: 30px;
            width: 100%;
            border-collapse: collapse;
        }
        .grade-table th, .grade-table td {
            padding: 10px;
            border: 1px solid #ddd;
            text-align: center;
        }
        .grade-table th {
            background-color: #004080;
            color: white;
        }
        .grade-table tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        @media (max-width: 600px) {
            .course {
                flex-direction: column;
                align-items: flex-start;
            }
            select, button.delete {
                width: 100%; /* Still full width on mobile */
                margin: 5px 0;
            }
            label {
                width: auto;
                margin-bottom: 5px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="uwi_logo_1.png" alt="UWI Logo" class="logo">
        <h1></h1>
        <p>Calculate your GPA easily with this tool designed for University of the West Indies students. Select your grades and credits below.</p>
        <div id="courses">
            <div class="course">
                <label>Course 1:</label>
                <select class="grade">
                    <option value="" selected>Select Grade</option>
                    <option value="A+">A+</option>
                    <option value="A">A</option>
                    <option value="A-">A-</option>
                    <option value="B+">B+</option>
                    <option value="B">B</option>
                    <option value="B-">B-</option>
                    <option value="C+">C+</option>
                    <option value="C">C</option>
                    <option value="F1">F1</option>
                    <option value="F2">F2</option>
                    <option value="F3">F3</option>
                </select>
                <select class="credits">
                    <option value="" selected>Select Credits</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                    <option value="6">6</option>
                </select>
                <button class="delete" onclick="deleteCourse(this)">Delete</button>
            </div>
            <div class="course">
                <label>Course 2:</label>
                <select class="grade">
                    <option value="" selected>Select Grade</option>
                    <option value="A+">A+</option>
                    <option value="A">A</option>
                    <option value="A-">A-</option>
                    <option value="B+">B+</option>
                    <option value="B">B</option>
                    <option value="B-">B-</option>
                    <option value="C+">C+</option>
                    <option value="C">C</option>
                    <option value="F1">F1</option>
                    <option value="F2">F2</option>
                    <option value="F3">F3</option>
                </select>
                <select class="credits">
                    <option value="" selected>Select Credits</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                    <option value="6">6</option>
                </select>
                <button class="delete" onclick="deleteCourse(this)">Delete</button>
            </div>
        </div>
        <div class="button-group">
            <button class="add" onclick="addCourse()">Add Another Course</button>
            <button class="calculate" onclick="calculateGPA()">Calculate GPA</button>
        </div>
        <div id="result"></div>
        <table class="grade-table">
            <thead>
                <tr>
                    <th>Grade</th>
                    <th>Quality Points per Credit Hour</th>
                    <th>Percentage Range</th>
                </tr>
            </thead>
            <tbody>
                <tr><td>A+</td><td>4.3</td><td>90-100</td></tr>
                <tr><td>A</td><td>4.0</td><td>80-89</td></tr>
                <tr><td>A-</td><td>3.7</td><td>75-79</td></tr>
                <tr><td>B+</td><td>3.3</td><td>70-74</td></tr>
                <tr><td>B</td><td>3.0</td><td>65-69</td></tr>
                <tr><td>B-</td><td>2.7</td><td>60-64</td></tr>
                <tr><td>C+</td><td>2.3</td><td>55-59</td></tr>
                <tr><td>C</td><td>2.0</td><td>50-54</td></tr>
                <tr><td>F1</td><td>1.7</td><td>40-49</td></tr>
                <tr><td>F2</td><td>1.3</td><td>30-39</td></tr>
                <tr><td>F3</td><td>0.0</td><td>0-29</td></tr>
            </tbody>
        </table>
    </div>

    <script>
        const gradePoints = {
            'A+': 4.3,
            'A': 4.0,
            'A-': 3.7,
            'B+': 3.3,
            'B': 3.0,
            'B-': 2.7,
            'C+': 2.3,
            'C': 2.0,
            'F1': 1.7,
            'F2': 1.3,
            'F3': 0.0
        };

        function updateCourseNumbers() {
            const courses = document.getElementsByClassName('course');
            for (let i = 0; i < courses.length; i++) {
                const label = courses[i].getElementsByTagName('label')[0];
                label.innerText = `Course ${i + 1}:`;
            }
        }

        function addCourse() {
            const courseDiv = document.createElement('div');
            courseDiv.className = 'course';
            courseDiv.innerHTML = `
                <label>Course:</label>
                <select class="grade">
                    <option value="" selected>Select Grade</option>
                    <option value="A+">A+</option>
                    <option value="A">A</option>
                    <option value="A-">A-</option>
                    <option value="B+">B+</option>
                    <option value="B">B</option>
                    <option value="B-">B-</option>
                    <option value="C+">C+</option>
                    <option value="C">C</option>
                    <option value="F1">F1</option>
                    <option value="F2">F2</option>
                    <option value="F3">F3</option>
                </select>
                <select class="credits">
                    <option value="" selected>Select Credits</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                    <option value="6">6</option>
                </select>
                <button class="delete" onclick="deleteCourse(this)">Delete</button>
            `;
            document.getElementById('courses').appendChild(courseDiv);
            updateCourseNumbers();
        }

        function deleteCourse(button) {
            const courses = document.getElementsByClassName('course');
            if (courses.length > 1) {
                button.parentElement.remove();
                updateCourseNumbers();
            } else {
                alert('You must keep at least one course.');
            }
        }

        function calculateGPA() {
            const grades = document.getElementsByClassName('grade');
            const credits = document.getElementsByClassName('credits');
            let totalPoints = 0;
            let totalCredits = 0;

            for (let i = 0; i < grades.length; i++) {
                const grade = grades[i].value;
                const credit = parseInt(credits[i].value) || 0;

                if (gradePoints[grade] !== undefined && credit > 0) {
                    totalPoints += gradePoints[grade] * credit;
                    totalCredits += credit;
                } else if (grade !== '' || credits[i].value !== '') {
                    alert('Please select both a grade and credit hours for course ' + (i + 1));
                    return;
                }
            }

            if (totalCredits === 0) {
                document.getElementById('result').innerText = 'Please enter at least one valid course.';
                return;
            }

            const gpa = (totalPoints / totalCredits).toFixed(2);
            document.getElementById('result').innerText = `Your GPA is: ${gpa}`;
        }
    </script>
</body>
</html>
