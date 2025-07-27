<!DOCTYPE html>
<html>
<head>
  <title>College Chatbot</title>
</head>
<body>
  <div id="chat"></div>
  <input id="input" type="text" placeholder="Ask me anything..." />
  <button onclick="send()">Send</button>
  <script>
    function send() {
      const input = document.getElementById('input').value;
      fetch('/chat', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ message: input })
      })
      .then(res => res.json())
      .then(data => {
        document.getElementById('chat').innerHTML += <div>You: ${input}</div>;
        document.getElementById('chat').innerHTML += <div>Bot: ${data.reply}</div>;
        document.getElementById('input').value = '';
      });
    }
  </script>
</body>
</html>
