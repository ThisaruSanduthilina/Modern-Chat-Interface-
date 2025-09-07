# Vue Chat Interface

A sleek and modern chat interface built with Vue.js 3 that provides an intuitive messaging experience. This project demonstrates clean component architecture, responsive design principles, and smooth user interactions.

## ✨ Features

- **Responsive Design**: Adapts beautifully to any screen size
- **Real-time Simulation**: Experience live chat with simulated bot responses  
- **Smooth Animations**: Polished transitions and micro-interactions
- **Keyboard Shortcuts**: Press Enter to send, Shift+Enter for new lines
- **Auto-scroll**: Messages automatically scroll into view
- **Smart Input**: Dynamic textarea that grows with your message
- **Modern UI**: Clean design with thoughtful color choices and spacing

## 🚀 Quick Start

### Prerequisites

Make sure you have Node.js installed on your machine (version 14 or higher recommended).

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/vue-chat-interface.git
   cd vue-chat-interface
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Open your browser** and navigate to `http://localhost:3000`

## 📁 Project Structure

The codebase follows Vue.js best practices with clear separation of concerns:

```
src/
├── components/
│   ├── ChatHeader.vue     # Top bar with user info and status
│   ├── MessageList.vue    # Scrollable chat history
│   └── MessageInput.vue   # Message composition area
├── App.vue               # Root component with chat logic
└── main.js              # Application entry point
```

## 🎯 How It Works

The chat interface consists of three main components:

- **ChatHeader**: Displays the chat title, online status, and user avatar
- **MessageList**: Renders all messages with timestamps and sender identification  
- **MessageInput**: Handles user input with send functionality and keyboard shortcuts

Messages are stored in the main App component and passed down to child components. The bot responds automatically to certain keywords and provides contextual responses.

## 🛠 Development

### Available Scripts

- `npm run dev` - Start development server with hot reload
- `npm run build` - Create production build
- `npm run preview` - Preview production build locally

### Customizing the Bot

You can enhance the bot's intelligence by modifying the `simulateBotResponse` method in `App.vue`:

```javascript
simulateBotResponse(userMessage) {
  // Add your custom logic here
  // Connect to AI APIs, implement NLP, etc.
}
```

## 🎨 Styling

The interface uses modern CSS with:
- CSS Grid and Flexbox for layouts
- CSS custom properties for theming
- Smooth transitions and animations
- Mobile-first responsive design

## 🌐 Browser Support

Works on all modern browsers:
- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation

---

Built with ❤️ using Vue.js
