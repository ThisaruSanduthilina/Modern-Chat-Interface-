<template>
  <div class="message-input-container">
    <div class="input-wrapper">
      <textarea
        v-model="message"
        @keydown="handleKeyDown"
        @input="adjustHeight"
        ref="textarea"
        placeholder="Type your message..."
        class="message-input"
        rows="1"
      ></textarea>
      <button
        @click="sendMessage"
        :disabled="!message.trim() || isSending"
        class="send-button"
        :class="{ 'sending': isSending }"
      >
        <svg v-if="!isSending" width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M22 2L11 13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M22 2L15 22L11 13L2 9L22 2Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        <div v-else class="spinner"></div>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MessageInput',
  data() {
    return {
      message: '',
      isSending: false
    }
  },
  methods: {
    sendMessage() {
      if (!this.message.trim() || this.isSending) return

      this.isSending = true
      this.$emit('send-message', this.message.trim())
      this.message = ''
      
      // Reset textarea height
      this.$nextTick(() => {
        this.adjustHeight()
      })

      // Reset sending state after a delay
      setTimeout(() => {
        this.isSending = false
      }, 500)
    },
    handleKeyDown(event) {
      if (event.key === 'Enter' && !event.shiftKey) {
        event.preventDefault()
        this.sendMessage()
      }
    },
    adjustHeight() {
      const textarea = this.$refs.textarea
      if (textarea) {
        textarea.style.height = 'auto'
        const maxHeight = 120 // Max 5 rows approximately
        textarea.style.height = Math.min(textarea.scrollHeight, maxHeight) + 'px'
      }
    }
  },
  mounted() {
    this.adjustHeight()
  }
}
</script>

<style scoped>
.message-input-container {
  padding: 20px;
  background: white;
  border-top: 1px solid #e5e7eb;
  display: flex;
  justify-content: center;
}

.input-wrapper {
  display: flex;
  align-items: flex-end;
  gap: 12px;
  background: #f8fafc;
  border: 2px solid #e5e7eb;
  border-radius: 24px;
  padding: 8px 12px;
  transition: border-color 0.2s ease;
  width: 100%;
  max-width: 800px;
}

.input-wrapper:focus-within {
  border-color: #667eea;
  background: white;
}

.message-input {
  flex: 1;
  border: none;
  outline: none;
  background: transparent;
  font-family: inherit;
  font-size: 16px;
  line-height: 1.5;
  padding: 8px 12px;
  resize: none;
  color: #374151;
}

.message-input::placeholder {
  color: #9ca3af;
}

.send-button {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  cursor: pointer;
  transition: all 0.2s ease;
  flex-shrink: 0;
}

.send-button:hover:not(:disabled) {
  transform: scale(1.05);
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
}

.send-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
}

.send-button.sending {
  animation: pulse 1s infinite;
}

.spinner {
  width: 16px;
  height: 16px;
  border: 2px solid transparent;
  border-top: 2px solid white;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes pulse {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
