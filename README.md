<!DOCTYPE html>
<html>
<head>
    <title>SS1 Students Chat</title>
    <style>
        body{
            font-family: Arial, sans-serif;
            background:#f0f2f5;
            display:flex;
            justify-content:center;
            align-items:center;
            height:100vh;
        }

        .container{
            background:white;
            padding:20px;
            border-radius:10px;
            width:400px;
            box-shadow:0 0 10px rgba(0,0,0,0.2);
        }

        .chat-box{
            display:none;
        }

        #messages{
            height:300px;
            border:1px solid #ddd;
            overflow-y:auto;
            padding:10px;
            margin-bottom:10px;
        }

        button{
            background:#007bff;
            color:white;
            border:none;
            padding:10px;
            cursor:pointer;
        }

        input{
            padding:10px;
            width:100%;
            margin-bottom:10px;
        }
    </style>
</head>
<body>

<div class="container">

    <!-- Join Section -->
    <div id="joinSection">
        <h2>SS1 Students Chat</h2>

        <input type="email" id="email" placeholder="Enter your email" required>

        <button onclick="joinChat()">Join Group</button>
    </div>

    <!-- Chat Section -->
    <div class="chat-box" id="chatSection">
        <h3>Welcome <span id="userEmail"></span></h3>

        <div id="messages"></div>

        <input type="text" id="messageInput" placeholder="Type message...">

        <button onclick="sendMessage()">Send</button>
    </div>

</div>

<script>

let currentUser = "";

function joinChat(){
    let email = document.getElementById("email").value;

    if(email === ""){
        alert("Please enter your email.");
        return;
    }

    currentUser = email;

    document.getElementById("joinSection").style.display = "none";
    document.getElementById("chatSection").style.display = "block";

    document.getElementById("userEmail").innerText = email;
}

function sendMessage(){

    let input = document.getElementById("messageInput");
    let message = input.value;

    if(message.trim() === "") return;

    let messages = document.getElementById("messages");

    let div = document.createElement("div");

    div.innerHTML = "<strong>" + currentUser + ":</strong> " + message;

    messages.appendChild(div);

    input.value = "";

    messages.scrollTop = messages.scrollHeight;
}

</script>

</body>
</html>
