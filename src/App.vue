<template>
  <div class="d-flex vh-100" id="wrapper">
    <!-- Sidebar -->
     <sidNav />
    <!-- Main Content -->
    <div class="flex-grow-1 d-flex flex-column">
      <headers />
      <chatBody />
    </div>
  </div>
</template>
<script setup>
import sidNav from "@/components/sideNav.vue";
import headers from "@/components/pageHeader.vue";
import chatBody from "@/components/chatBody.vue";
</script>