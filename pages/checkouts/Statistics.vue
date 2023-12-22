<template>
    <v-container>
      <CheckoutSidebar />
      <div class="Statistics-module">
        <div class="Statistics-module__content">
          <b>No data found</b>
          <br>
          <p>You have no active integrations of 3D tools.</p>
        </div>
      </div>
    </v-container>
  </template>
  <script>
  export default {
    data: () => ({}),
  };
  </script>
  <style scoped>
  
  .Statistics-module__content {
    background: #fff;
    padding: 30px;
    margin: 20px 0;
  }
  </style>