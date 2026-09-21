# HTML Forms: A Complete Deep Dive

HTML **forms** are one of the most powerful and widely used features of web development. They act as the bridge between the user and the server — allowing users to input data, which is then processed, stored, or acted upon.

---

## 1. What is a Form?

A **form** in HTML is a container that holds interactive controls where users can enter data. Examples include:

- Login forms (username & password)
- Sign-up forms (name, email, password, etc.)
- Search bars
- Feedback/contact forms
- Checkout pages (address, payment info)

Forms are defined using the `<form>` element.

```html
<form action="/submit" method="POST">
  <!-- form elements go here -->
</form>

```

### Attributes of `<form>`:

- **action**: The URL where form data is sent.
- **met hod**: HTTP method (commonly `GET` or `POST`).
    - `GET`: Appends data to the URL (used for searches).
    - `POST`: Sends data securely in the request body (used for login, signup, payments).
- **target**: Where to display the response (default `_self`, can be `_blank`, `_parent`, etc.).
- **enctype**: Specifies encoding type (e.g., `multipart/form-data` for file uploads).

---

## 2. Basic Input Types

The `<input>` tag is the most versatile element inside a form. Different types create different controls.

### 2.1 Text Input

```html
<label for="username">Username:</label>
<input type="text" id="username" name="username" placeholder="Enter your username">

```

- `placeholder` shows hint text.
- `name` is the key by which data is sent.

### 2.2 Password Input

```html
<label for="password">Password:</label>
<input type="password" id="password" name="password">

```

- Characters are hidden with dots/bullets.

### 2.3 Email & URL

```html
<input type="email" name="user_email" placeholder="Enter email">
<input type="url" name="website" placeholder="Enter website URL">

```

- Browser validates email/URL format automatically.

### 2.4 Number

```html
<input type="number" name="age" min="1" max="100">

```

### 2.5 Date & Time

```html
<input type="date" name="dob">
<input type="time" name="meeting_time">
<input type="datetime-local" name="event">

```

### 2.6 Radio Buttons

```html
<label><input type="radio" name="gender" value="male"> Male</label>
<label><input type="radio" name="gender" value="female"> Female</label>

```

- Only one option can be selected per group (same `name`).

### 2.7 Checkboxes

```html
<label><input type="checkbox" name="subscribe" value="yes"> Subscribe to newsletter</label>

```

- Multiple checkboxes can be selected.

### 2.8 File Upload

```html
<input type="file" name="resume" accept=".pdf,.docx">

```

---

## 3. Other Form Controls

### 3.1 Dropdown (Select)

```html
<select name="country">
  <option value="india">India</option>
  <option value="usa">USA</option>
  <option value="uk">UK</option>
</select>

```

### 3.2 Textarea

```html
<textarea name="feedback" rows="5" cols="30" placeholder="Write your feedback..."></textarea>

```

### 3.3 Buttons

```html
<input type="submit" value="Submit">
<input type="reset" value="Reset">
<button type="button">Click Me</button>

```

---

## 4. Form Attributes for Input Elements

- **required** → Field must be filled before submission.
- **readonly** → Value cannot be changed.
- **disabled** → Field is disabled.
- **maxlength** → Limits number of characters.
- **pattern** → Regex validation.
- **autofocus** → Field gets focus on page load.

Example:

```html
<input type="text" name="pin" pattern="[0-9]{6}" placeholder="Enter 6-digit PIN" required>

```

---

## 5. Form Validation

### HTML5 Validation:

- Automatically checks email, URL, number, required, etc.
- Example:

```html
<input type="email" name="user_email" required>

```

### Custom Validation:

Using `pattern` attribute or JavaScript.

```html
<input type="text" name="username" pattern="[A-Za-z0-9]{5,}" title="At least 5 characters">

```

---

## 6. Example: Complete Registration Form

Here’s a **realistic example** combining all concepts.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Registration Form</title>
</head>
<body>
  <h2>User Registration</h2>
  <form action="/submit" method="POST" enctype="multipart/form-data">

    <label for="fname">First Name:</label>
    <input type="text" id="fname" name="first_name" required><br><br>

    <label for="lname">Last Name:</label>
    <input type="text" id="lname" name="last_name" required><br><br>

    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required><br><br>

    <label for="password">Password:</label>
    <input type="password" id="password" name="password" minlength="6" required><br><br>

    <label for="gender">Gender:</label>
    <input type="radio" name="gender" value="male"> Male
    <input type="radio" name="gender" value="female"> Female
    <input type="radio" name="gender" value="other"> Other<br><br>

    <label for="dob">Date of Birth:</label>
    <input type="date" id="dob" name="dob"><br><br>

    <label for="country">Country:</label>
    <select id="country" name="country">
      <option value="">--Select--</option>
      <option value="india">India</option>
      <option value="usa">USA</option>
      <option value="uk">UK</option>
    </select><br><br>

    <label for="resume">Upload Resume:</label>
    <input type="file" id="resume" name="resume" accept=".pdf,.doc,.docx"><br><br>

    <label for="bio">Short Bio:</label><br>
    <textarea id="bio" name="bio" rows="4" cols="40"></textarea><br><br>

    <label>
      <input type="checkbox" name="terms" required> I agree to the Terms & Conditions
    </label><br><br>

    <input type="submit" value="Register">
    <input type="reset" value="Clear">

  </form>
</body>
</html>

```

---

## 7. Analogy: Form as a Letter

Think of a **form** like sending a letter:

- The `<form>` is the **envelope**.
- Each `<input>` is a **blank space** to be filled (name, address, etc.).
- The `action` is the **address** of the receiver.
- The `method` is the **delivery type** (fast mail = POST, postcard = GET).
- The `submit` button is the **postman** delivering the letter.