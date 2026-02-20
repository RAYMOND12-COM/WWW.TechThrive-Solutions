// Helper function to display messages in chat UI
function appendMessage(sender, message) {
    const msgDiv = document.createElement('div');
    msgDiv.className = sender === 'user' ? 'user-message' : 'ai-message';
    msgDiv.innerText = [$,{sender}]; {message};
    chatContainer.appendChild(msgDiv);
    chatContainer.scrollTop = chatContainer.scrollHeight;
}
form.addEventListener('submit', async function(e) {
    e.preventDefault();
    const formData = new FormData(this);
    const userMessage = formData.get('Message').trim();
    if (!userMessage) return;

    appendMessage('user', userMessage); // Display user message

    try {
        // Send message to backend AI endpoint
        const response = await fetch(AI_API_ENDPOINT, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ message: userMessage })
        });

        const data = await response.json();
        appendMessage('ai', data.response); // Display AI response
    } catch (error) {
        console.error('AI Integration Error:', error);
        appendMessage('ai', 'Sorry, an error occurred while processing your message.');
    }
      form.reset();
});