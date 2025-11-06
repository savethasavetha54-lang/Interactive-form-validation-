 Interactive Form Validation

Overview

This project demonstrates an interactive form validation system using HTML, CSS, and JavaScript. It validates user inputs in real-time and provides instant feedback through error and success messages. The goal is to ensure that form data is accurate and properly formatted before submission.

Objective

The main objective of this project is to:

Implement client-side validation using JavaScript.

Provide real-time feedback to the user while filling out the form.

Enhance user experience by preventing invalid submissions.

Serve as a simple and effective demonstration for Mudhalvan practical evaluation.


Features

Validates name, email, and password fields.

Checks email format using Regular Expressions.

Ensures password strength (minimum 8 characters and at least one number).

Displays dynamic error messages and success feedback.

Uses simple, responsive styling for clarity.


Technologies Used

HTML5 — for form structure

CSS3 — for styling and layout

JavaScript (Vanilla JS) — for validation logic


Folder Structure

interactive-form-validation/
│
├── index.html       # Main HTML form file  
├── styles.css       # Styling for form and validation messages  
└── script.js        # JavaScript validation logic

How to Run

1. Save all files in the same folder.


2. Open index.html in any web browser.


3. Enter form details and observe live validation feedback.




---

Sample Code

index.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Interactive Form Validation</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <h1>Interactive Form Validation</h1>
  <form id="regForm" novalidate>
    <label>
      Name
      <input type="text" id="name" required>
      <small class="error" data-for="name"></small>
    </label>

    <label>
      Email
      <input type="email" id="email" required>
      <small class="error" data-for="email"></small>
    </label>

    <label>
      Password
      <input type="password" id="password" required>
      <small class="error" data-for="password"></small>
    </label>

    <button type="submit">Submit</button>
  </form>

  <script src="script.js"></script>
</body>
</html>


---

script.js

const form = document.getElementById('regForm');
const nameEl = document.getElementById('name');
const emailEl = document.getElementById('email');
const passEl = document.getElementById('password');

function showError(el, msg) {
  const small = document.querySelector(`small[data-for="${el.id}"]`);
  small.textContent = msg;
  el.classList.add('invalid');
}

function clearError(el) {
  const small = document.querySelector(`small[data-for="${el.id}"]`);
  small.textContent = '';
  el.classList.remove('invalid');
}

function validateEmail(value) {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value);
}

nameEl.addEventListener('input', () => {
  if (nameEl.value.trim().length < 3) showError(nameEl, 'Name must be at least 3 characters');
  else clearError(nameEl);
});

emailEl.addEventListener('input', () => {
  if (!validateEmail(emailEl.value)) showError(emailEl, 'Invalid email format');
  else clearError(emailEl);
});

passEl.addEventListener('input', () => {
  if (passEl.value.length < 8) showError(passEl, 'Password must be at least 8 characters');
  else if (!/\d/.test(passEl.value)) showError(passEl, 'Password must contain at least one number');
  else clearError(passEl);
});

form.addEventListener('submit', (e) => {
  e.preventDefault();
  if (nameEl.classList.contains('invalid') || 
      emailEl.classList.contains('invalid') || 
      passEl.classList.contains('invalid')) {
    alert('Please fix the errors before submitting.');
    return;
  }
  alert('Form submitted successfully!');
});


---

styles.css

body {
  font-family: Arial, sans-serif;
  padding: 20px;
  max-width: 480px;
  margin: auto;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 15px;
}

input {
  width: 100%;
  padding: 8px;
  margin-top: 4px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  width: 100%;
  padding: 10px;
  border: none;
  background-color: #007bff;
  color: white;
  font-size: 16px;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.error {
  color: red;
  font-size: 0.9em;
  height: 1em;
  display: block;
}

input.invalid {
  border-color: red;
}


---

Viva / Presentation Points

The novalidate attribute disables default browser validation.

Real-time validation is implemented using the input event listener.

Regular expressions are used for pattern matching (email format).

Client-side validation improves user experience but server-side validation is still required for security.

Possible improvements include adding confirm password fields, strength meters, and accessibility enhancements.



---

Conclusion

This project illustrates a simple yet effective way to perform interactive client-side form validation using JavaScript. It enhances form usability, improves data accuracy, and demonstrates essential front-end validation techniques suitable for any web-based project or examination
