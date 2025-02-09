# Chatbot Using HTML, CSS, and JavaScript

## Overview
This project is a web-based chatbot that utilizes JavaScript for handling user interactions and API requests. The front-end is built with HTML and CSS, while JavaScript manages the chatbot logic.

## Features
- Interactive chatbot interface
- AI-powered responses using an external API
- User-friendly and responsive UI
- Secure API integration

## Technologies Used
- **Front-end:** HTML, CSS
- **Back-end:** JavaScript (Node.js for API handling)

## Installation and Setup

### Prerequisites
Ensure you have the following installed on your system:
- Node.js
- A chatbot API key (if using an AI API)
- Basic knowledge of HTML, CSS, and JavaScript

### Steps to Set Up the Project
1. **Clone the Repository**
   ```sh
   git clone https://github.com/your-repo/chatbot.git
   cd chatbot
   ```
2. **Set Up the Front-End**
   - Place `index.html` and `styles.css` in the root directory.
3. **Configure the Back-End**
   - Use JavaScript to handle API requests and responses.
4. **Obtain an API Key**
   - Sign up at the AI API provider's official website.
   - Store the key securely in your JavaScript application.
5. **Run the Application**
   - Open `index.html` in your browser and start chatting!

## Sample Code

### HTML (`index.html`)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chatbot</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="chat-container">
        <div id="chat-box"></div>
        <input type="text" id="user-input" placeholder="Type a message...">
        <button onclick="sendMessage()">Send</button>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

### CSS (`styles.css`)
```css
body {
    font-family: Arial, sans-serif;
    text-align: center;
}
.chat-container {
    width: 300px;
    margin: auto;
    padding: 10px;
    border: 1px solid #ccc;
}
```

### JavaScript (`script.js`)
```javascript
async function sendMessage() {
    const userInput = document.getElementById("user-input").value;
    const chatBox = document.getElementById("chat-box");
    
    chatBox.innerHTML += `<p>User: ${userInput}</p>`;
    document.getElementById("user-input").value = "";

    const response = await fetch("https://api.example.com/chat", {
        method: "POST",
        headers: {
            "Content-Type": "application/json"
        },
        body: JSON.stringify({ message: userInput })
    });

    const data = await response.json();
    chatBox.innerHTML += `<p>Bot: ${data.response}</p>`;
}

