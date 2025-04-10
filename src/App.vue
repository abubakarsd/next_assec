<template>
  <div class="d-flex" id="wrapper">
    <div class="bg-light text-white" style="width: 350px; min-height: 100vh;">
      <div class="header-page d-flex justify-content-between text-white p-2">
        <h5 class="page-title p-2">Chats</h5>
        <span class="text-end p-2">0</span>
      </div>
      <ul class="nav flex-column">
        <li class="nav-item active-nav">
          <a class="nav-link text-white" href="#" @click="activeComponent = 'Users'">
            <div class="contents">
              <div class="d-flex justify-content-between">
                <div class="d-flex align-items-center">
                  <img src="@/assets/images/Ellipse 3.png" alt="user" class="rounded-circle me-2 avater-image" width="40" height="40">
                  <p class="text-truncate text-muted user-name">Akinpelu Babajide Akinloye <br><small class="pre-msg">Hello, Have put a call through and am wating for you</small></p>
                </div>
              </div>
            </div>
          </a>
        </li>
        <li class="nav-item">
          <a class="nav-link text-white" href="#" @click="activeComponent = 'Users'">
            <div class="contents">
              <div class="d-flex justify-content-between">
                <div class="d-flex align-items-center">
                  <img src="@/assets/images/Ellipse 4.png" alt="user" class="rounded-circle me-2 avater-image" width="40" height="40">
                  <p class="text-truncate text-muted user-name">Akinpelu Babajide Akinloye <br><small class="pre-msg">Hello, Have put a call through and am wating for you</small></p>
                </div>
              </div>
            </div>
          </a>
        </li>
        <li class="nav-item">
          <a class="nav-link text-white" href="#" @click="activeComponent = 'Users'">
            <div class="contents">
              <div class="d-flex justify-content-between">
                <div class="d-flex align-items-center">
                  <img src="@/assets/images/Ellipse 3 (2).png" alt="user" class="rounded-circle me-2 avater-image" width="40" height="40">
                  <p class="text-truncate text-muted user-name">Akinpelu Babajide Akinloye <br><small class="pre-msg">Hello, Have put a call through and am wating for you</small></p>
                </div>
              </div>
            </div>
          </a>
        </li>
        
      </ul>
    </div>
  </div>
  <headers/>
<chatApp />

</template>
<script setup>
import chatApp from '@/components/chatApp.vue'
import headers from '@/components/pageHeader.vue'
</script>
<style>
.header-page {
  background-color: #704EB9;
}
.active-nav {
  background-color: #F6F2FF;
}
.avater-image {
  border: 2px solid #704EB9;
}
.user-name {
  font-size: 12px;
}
.pre-msg {
  font-size: 10px;
}
</style>