# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  


// HTML part
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>JavaScript Event Playground 🎉</title>
  <!-- Link to external CSS file -->
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <h1>🎉 Welcome to the JavaScript Playground 🎉</h1>

  <!-- Button for click event -->
  <button id="clickMeBtn">Click Me!</button>

  <!-- Div for hover effect -->
  <div id="hoverArea">Hover over me!</div>

  <!-- Input for keypress detection -->
  <input type="text" id="keyInput" placeholder="Type something...">

  <!-- Secret double-click box -->
  <div id="secretBox">Double-click me for a secret! 🤫</div>

  <!-- Button to change its own color -->
  <button id="colorChangeBtn">Change my color</button>

  <!-- Simple image gallery with a button -->
  <div class="gallery">
    <img id="galleryImage" src="https://via.placeholder.com/300x200" alt="Gallery Image">
    <button id="nextImageBtn">Next Image</button>
  </div>

  <!-- Simple tabs setup -->
  <div class="tabs">
    <!-- Tab buttons -->
    <button class="tab" onclick="openTab('tab1')">Tab 1</button>
    <button class="tab" onclick="openTab('tab2')">Tab 2</button>

    <!-- Tab content sections -->
    <div id="tab1" class="tabContent">This is Tab 1 content.</div>
    <div id="tab2" class="tabContent">This is Tab 2 content.</div>
  </div>

  <!-- Form for validation -->
  <form id="sampleForm">
    <input type="text" id="name" placeholder="Name" required>
    <input type="email" id="email" placeholder="Email" required>
    <input type="password" id="password" placeholder="Password (min 8 chars)" required>
    <button type="submit">Submit</button>
    <p id="formFeedback"></p>
  </form>

  <!-- Link to external JavaScript file -->
  <script src="script.js"></script>
</body>
</html>


//CSS part
/* Set default font and center align text */
body {
  font-family: sans-serif;
  text-align: center;
  padding: 20px;
}

/* Style for all buttons */
button {
  padding: 10px 20px;
  margin: 10px;
  border-radius: 8px;
}

/* Style for hover area div */
#hoverArea {
  padding: 20px;
  margin: 10px;
  background: lightgray;
}

/* Center the image in gallery */
.gallery img {
  display: block;
  margin: 0 auto;
}

/* Hide all tab content by default */
.tabContent {
  display: none;
  margin-top: 10px;
}


//JAVASCRIPT part
// Event Handling 🎈

// Button click event
document.getElementById("clickMeBtn").addEventListener("click", () => {
  alert("Button Clicked!");
});

// Change background color when hovering over the div
document.getElementById("hoverArea").addEventListener("mouseover", () => {
  document.getElementById("hoverArea").style.backgroundColor = "lightblue";
});

// Detect and log key presses in the input field
document.getElementById("keyInput").addEventListener("keypress", (e) => {
  console.log(`You pressed: ${e.key}`);
});

// Secret action triggered on double-click
document.getElementById("secretBox").addEventListener("dblclick", () => {
  alert("🎉 Secret Action Activated!");
});

// Interactive Elements 🎮

// Change button background color when clicked
document.getElementById("colorChangeBtn").addEventListener("click", () => {
  document.getElementById("colorChangeBtn").style.backgroundColor = "orange";
});

// Image gallery with multiple images
let images = [
  "https://via.placeholder.com/300x200?text=Image+1",
  "https://via.placeholder.com/300x200?text=Image+2",
  "https://via.placeholder.com/300x200?text=Image+3"
];
let index = 0;

// Change to next image when button is clicked
document.getElementById("nextImageBtn").addEventListener("click", () => {
  index = (index + 1) % images.length;
  document.getElementById("galleryImage").src = images[index];
});

// Function to show selected tab and hide others
function openTab(tabId) {
  // Hide all tab content sections
  document.querySelectorAll('.tabContent').forEach(tab => tab.style.display = "none");
  // Display the selected tab content
  document.getElementById(tabId).style.display = "block";
}

// Form Validation 📋✅

// Handle form submission
document.getElementById("sampleForm").addEventListener("submit", (e) => {
  e.preventDefault(); // Prevent default form submission

  // Get form input values
  let name = document.getElementById("name").value.trim();
  let email = document.getElementById("email").value.trim();
  let password = document.getElementById("password").value;

  // Initialize feedback message
  let feedback = "";

  // Validation checks
  if (name === "" || email === "" || password === "") {
    feedback = "❌ All fields are required!";
  } else if (!email.includes("@")) {
    feedback = "❌ Invalid email format!";
  } else if (password.length < 8) {
    feedback = "❌ Password must be at least 8 characters!";
  } else {
    feedback = "✅ Form submitted successfully!";
  }

  // Display feedback message
  document.getElementById("formFeedback").textContent = feedback;
});

// Bonus: Real-time Password Validation

// Check password length as user types
document.getElementById("password").addEventListener("input", () => {
  let password = document.getElementById("password").value;
  let feedback = document.getElementById("formFeedback");

  if (password.length >= 8) {
    feedback.textContent = "✅ Password strength good.";
  } else {
    feedback.textContent = "❌ Password too short.";
  }
});


