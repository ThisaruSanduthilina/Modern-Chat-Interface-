<template>
  <div class="chat-container">
    <ChatHeader />
    <MessageList :messages="messages" />
    <MessageInput @send-message="handleSendMessage" />
  </div>
</template>

<script>
import ChatHeader from './components/ChatHeader.vue'
import MessageList from './components/MessageList.vue'
import MessageInput from './components/MessageInput.vue'

export default {
  name: 'App',
  components: {
    ChatHeader,
    MessageList,
    MessageInput
  },
  data() {
    return {
      messages: [
        {
          id: 1,
          text: 'Hello! Welcome to the chat interface.',
          sender: 'bot',
          timestamp: new Date('2025-09-07T10:00:00')
        },
        {
          id: 2,
          text: 'How can I help you today?',
          sender: 'bot',
          timestamp: new Date('2025-09-07T10:00:30')
        }
      ]
    }
  },
  methods: {
    handleSendMessage(message) {
      // Add user message
      const userMessage = {
        id: Date.now(),
        text: message,
        sender: 'user',
        timestamp: new Date()
      }
      this.messages.push(userMessage)

      // Simulate bot response after a short delay
      setTimeout(() => {
        this.simulateBotResponse(message)
      }, 1000)
    },
    simulateBotResponse(userMessage) {
      const botResponses = [
        "That's interesting! Tell me more.",
        "I understand what you're saying.",
        "Thanks for sharing that with me.",
        "That sounds great!",
        "I'm here to help with any questions you have.",
        "What would you like to know next?",
        "I appreciate you taking the time to chat."
      ]

      // Simple keyword-based responses
      let response
      if (userMessage.toLowerCase().includes('hello') || userMessage.toLowerCase().includes('hi')) {
        response = "Hello! Nice to meet you!"
      } else if (userMessage.toLowerCase().includes('how are you')) {
        response = "I'm doing well, thank you for asking! How are you?"
      } else if (userMessage.toLowerCase().includes('help')) {
        response = "I'm here to help! What do you need assistance with?"
      } else if (userMessage.toLowerCase().includes('bye')) {
        response = "Goodbye! Have a great day!"
      } else {
        response = botResponses[Math.floor(Math.random() * botResponses.length)]
      }

      const botMessage = {
        id: Date.now() + 1,
        text: response,
        sender: 'bot',
        timestamp: new Date()
      }
      this.messages.push(botMessage)
    }
  }
}
</script>

<style scoped>
.chat-container {
  display: flex;
  flex-direction: column;
  height: 100vh;
  width: 100vw;
  background: white;
  border-radius: 0;
  box-shadow: none;
  overflow: hidden;
}
</style>
