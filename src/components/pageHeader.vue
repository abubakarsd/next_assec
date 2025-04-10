<template>
  <div class="bg-white shadow-sm w-100">
    <div class="d-flex justify-content-between align-items-center p-3">
      <div class="d-flex align-items-center">
        <div class="position-relative me-3">
          <img
            src="@/assets/images/Ellipse 3.png"
            alt="user"
            class="rounded-circle avater-image"
            width="40"
            height="40"
          />
          <span class="status-indicator"></span>
        </div>
        <div>
          <p class="mb-0 fw-bold small text-truncate text-muted">Akinpelu Babajide Akinloye</p>
          <small class="text-muted">Online</small>
        </div>
      </div>

      <div class="d-flex align-items-center gap-4">
        <button class="btn btn-link text-muted p-1">
          <i class="bi bi-telephone text-muted fs-5"></i>
        </button>
        <button class="btn btn-link text-muted p-1">
          <i class="bi bi-camera-video text-muted fs-5"></i>
        </button>
        <button class="btn btn-send-msg">Send Money</button>
        <button class="btn btn-outline-secondary rounded-circle w-5 h-5">
          <i class="bi bi-three-dots fs-5"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.avater-image {
  border: 2px solid #704EB9;
}

.btn-send-msg {
  background-color: #704EB9;
  color: white;
  padding: 0.5rem 1.2rem;
  font-size: 14px;
  border: none; /* Remove default button border */
  }
.status-indicator {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: 2px solid white;
  background-color: #704EB9;
}
</style>