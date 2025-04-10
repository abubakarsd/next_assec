<template> 
    <!-- Sidebar -->
<div class="bg-white text-dark shadow-sm d-flex flex-column" style="width: 350px; height: 100vh;">
    <!-- Header Section -->
    <div class="header-page d-flex justify-content-between align-items-center p-3 text-white flex-shrink-0">
      <h5 class="m-0">Chats</h5>
      <span class="text-white">58</span>
    </div>
      <!-- Chat List (Scroll Area) -->
      <div class="overflow-auto flex-grow-1">
        <ul class="nav flex-column">
          <li
            v-for="(user, index) in users"
            :key="index"
            class="nav-item chat-item"
            :class="{ 'active-nav': active === index }"
            @mouseover="hover = index"
            @mouseleave="hover = null"
            @click="selectUser(index)"
          >
            <a class="nav-link p-3" href="#">
              <div class="d-flex align-items-start">
                <div class="position-relative me-3">
                  <img
                    :src="user.image"
                    alt="user"
                    class="rounded-circle avater-image"
                    width="45"
                    height="45"
                  />
                  <span
                    class="status-indicator"
                    :class="user.online ? 'bg-success' : 'bg-secondary'"
                  ></span>
                </div>
                <div class="flex-grow-1">
                  <p class="mb-1 fw-bold small text-truncate text-muted">{{ user.name }}</p>
                  <small
                    class="text-muted d-block message-truncate"
                    v-html="user.message"
                  ></small>
                </div>
                <div class="d-flex align-items-center justify-content-end">
                  <i v-if="user.send" class="bi bi-check-all me-2 text-muted"></i><span v-if="user.count > 0" class="badge rounded-pill text-white total-message-count">{{ user.count }}</span>
                </div>
              </div>
            </a>
          </li>
        </ul>
      </div>
      </div>
</template>
<script setup>
import { ref } from "vue";
const active = ref(null);
const hover = ref(null);

const users = [
  {
    name: "Akinpelu Babajide Akinloye",
    message: "Hello, Have put a call through and am waiting for you",
    time: "10:30 AM",
    image: "/src/assets/images/Ellipse 3.png",
    online: true,
    send: true,
    count: 0,
  },
  {
    name: "Adebayo Oluwatobi Johnson",
    message: "<i class='bi bi-trash'></i> <em>Message deleted</em>", // Italicized text
    time: "11:15 AM",
    image: "/src/assets/images/Ellipse 4.png",
    online: false,
    send: false,
    count: 0,
  },
  {
    name: "Akinpelu Babajide Akinloye",
    message: "Hello, Have put a call through and am waiting for you",
    time: "10:30 AM",
    image: "/src/assets/images/Ellipse 3 (2).png",
    online: true,
    send: false,
    count: 4,
  },
  {
    name: "Jane Doe",
    message: "<i class='bi bi-file-earmark-text'></i> <em>Shared a file</em>", // Italicized text
    time: "11:15 AM",
    image: "/src/assets/images/Ellipse 3 (5).png",
    online: false,
    send: true,
    count: 0,
  },
  {
    name: "Abubakar Ibrahim Musa",
    message: "Hello, Have put a call through and am waiting for you",
    time: "10:30 AM",
    image: "/src/assets/images/Ellipse 3.png",
    online: false,
    send: false,
    count: 2,
  },
  {
    name: "Jane Doe",
    message: "<i class='bi bi-camera-video'></i> <em>Shared a video</em>", // Italicized text
    time: "11:15 AM",
    image: "/src/assets/images/Ellipse 3.png",
    online: false,
    send: false,
    count: 1,
  },
  {
    name: "Michael Johnson",
    message: "<i class='bi bi-soundwave'></i> <em>Shared a voice note</em>", // Italicized text
    time: "9:45 AM",
    image: "/src/assets/images/Ellipse 3.png",
    online: true,
    send: false,
    count: 20,
  },
  {
    name: "Michael Johnson",
    message: "<i class='bi bi-music-note-beamed'></i> <em>Send audio</em>", // Italicized text
    time: "9:45 AM",
    image: "/src/assets/images/Ellipse 4.png",
    online: false,
    send: false,
    count: 0,
  },
  {
    name: "Akinpelu Babajide Akinloye",
    message: "Hello, Have put a call through and am waiting for you",
    time: "10:30 AM",
    image: "/src/assets/images/Ellipse 3 (4).png",
    online: true,
    send: false,
    count: 2,
  },
  {
    name: "Akinpelu Babajide Akinloye",
    message: "Hello, Have put a call through and am waiting for you",
    time: "10:30 AM",
    image: "/src/assets/images/Ellipse 3.png",
    online: false,
    send: false,
    count: 2,
  },
];

const selectUser = (index) => {
  active.value = index;
};
</script>

<style scoped>
.header-page {
  background-color: #704eb9;
}

.chat-item {
  transition: background-color 0.2s;
}

.chat-item:hover {
  background-color: #f6f2ff;
  cursor: pointer;
}

.active-nav {
  background-color: #f6f2ff !important;
}

.avater-image {
  border: 2px solid #704eb9;
}

.status-indicator {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: 2px solid white;
}

.text-truncate {
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.message-truncate {
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.nav-link {
  font-size: 14px;
}

.message-truncate em {
  font-style: italic;
}

.total-message-count {
  font-size: 12px;
  background-color: #704eb9;
}
</style>
