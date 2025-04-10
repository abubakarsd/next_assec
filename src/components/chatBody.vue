<template>
    <div class="chat-body d-flex flex-column h-100">
      <!-- Messages Area -->
      <div class="flex-grow-1 overflow-auto p-3 messages-area">
        <!-- Older Messages -->
        <div v-for="(msg, index) in messages.filter(m => m.date !== 'today')" :key="'old-'+index" class="mb-4">
          <div class="d-flex" :class="{ 'justify-content-end': msg.sender === 'me' }">
            <div class="chat-bubble" :class="msg.sender === 'me' ? 'me-msg' : 'other-msg'">
              <small>{{ msg.text }}</small>
            </div>
          </div>
          <div class="text-muted small mt-1" :class="{ 'text-end': msg.sender === 'me', 'text-start': msg.sender !== 'me' }">
            {{ msg.time }}
          </div>
        </div>
  
        <!-- Today Label -->
        <div class="text-center mb-3">
          <span class="badge bg-light text-dark px-3 py-2 shadow-sm rounded-pill">Today</span>
        </div>
  
        <!-- Today's Messages -->
        <div v-for="(msg, index) in messages.filter(m => m.date === 'today')" :key="'today-'+index" class="mb-4">
          <div class="d-flex" :class="{ 'justify-content-end': msg.sender === 'me' }">
            <div class="chat-bubble" :class="msg.sender === 'me' ? 'me-msg' : 'other-msg'">
              <small>{{ msg.text }}</small>
            </div>
          </div>
          <div class="text-muted small mt-1" :class="{ 'text-end': msg.sender === 'me', 'text-start': msg.sender !== 'me' }">
            {{ msg.time }}
          </div>
        </div>
      </div>
  
      <!-- Input Section -->
      <div class="p-3 bg-white input-area">
        <div class="d-flex align-items-center w-100">
          <div class="position-relative flex-grow-1 me-2">
            <i class="bi bi-emoji-smile emoji-icon position-absolute"></i>
            <input
              type="text"
              v-model="newMessage"
              class="form-control ps-5"
              placeholder="Type a message..."
            />
          </div>
          <button class="btn send-btn" @click="sendMessage">
            <i class="bi bi-send"></i>
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const messages = ref([
    {
      sender: 'other',
      text: "Hello peter i have been meaning to send you a message concerning the appointment with the federal ministry of health.",
      time: '08:30 AM',
      date: 'yesterday'
    },
    {
      sender: 'me',
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad ",
      time: '08:45 AM',
      date: 'yesterday'
    },
    {
      sender: 'other',
      text: "Hi",
      time: '08:55 AM',
      date: 'yesterday'
    },
    {
      sender: 'other',
      text: "Hello Peter, I have been meaning to send you a message concerning the appointment with the federal ministry of health.",
      time: '09:45 AM',
      date: 'today'
    },
    {
      sender: 'me',
      text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit...',
      time: '09:47 AM',
      date: 'today'
    },
    {
      sender: 'me',
      text: "Doing great, thanks!",
      time: '09:49 AM',
      date: 'today'
    }
  ])
  
  const newMessage = ref('')
  
  const sendMessage = () => {
    if (newMessage.value.trim()) {
      const now = new Date()
      const hours = now.getHours() % 12 || 12
      const minutes = now.getMinutes().toString().padStart(2, '0')
      const ampm = now.getHours() >= 12 ? 'PM' : 'AM'
      const timeString = `${hours}:${minutes} ${ampm}`
  
      messages.value.push({
        sender: 'me',
        text: newMessage.value,
        time: timeString,
        date: 'today'
      })
  
      newMessage.value = ''
    }
  }
  </script>
  
  <style scoped>
  .chat-body {
    position: relative;
    min-height: calc(100vh - 70px);
    background-image: url('@/assets/images/social-media-sketch-vector-seamless-600nw-1660950727.webp');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    z-index: 1;
  }
  .chat-body::before {
    content: "";
    position: absolute;
    inset: 0;
    background-color: rgba(224, 245, 235, 0.85);
    z-index: 2;
  }
  .chat-body > * {
    position: relative;
    z-index: 3;
  }
  .messages-area {
    scrollbar-width: thin;
    scrollbar-color: #ccc transparent;
  }
  .messages-area::-webkit-scrollbar {
    width: 6px;
  }
  .messages-area::-webkit-scrollbar-thumb {
    background-color: #ccc;
    border-radius: 5px;
  }
  .chat-bubble {
    padding: 10px 15px;
    border-radius: 18px;
    max-width: 75%;
    position: relative;
    word-wrap: break-word;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }
  .me-msg {
    background-color: #704eb9;
    color: #fff;
    border-bottom-right-radius: 1px;
  }
  .other-msg {
    background-color: #ffffff;
    color: #000;
    border-bottom-left-radius: 1px;
  }
  .input-area input {
    border-radius: 20px;
  }
  .input-area button {
    border-radius: 50%;
  }
  .emoji-icon {
    top: 50%;
    left: 15px;
    transform: translateY(-50%);
    color: #888;
    font-size: 1.2rem;
    pointer-events: none;
  }
  .send-btn {
    background-color: #704eb9;
    border-color: #704eb9;
    color: white;
  }
  .send-btn:hover {
    background-color: #5e3fa1;
    border-color: #5e3fa1;
  }
  .badge {
    font-weight: 500;
    font-size: 0.85rem;
  }
  </style>
  