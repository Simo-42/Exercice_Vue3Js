<template>
  <main>
      <Notification type="warning" title="Modal Window" 
      message="lorem ipsum dolor sit amet, 
      consectetur adipiscing elit ut aliqum, 
      purus sit amet luctus venenatis, lectus 
      magna fringilla urna, porttitor" />

      <Notification type="sucess" title="Modal Window"
      message="lorem ipsum dolor sit amet,
      consectetur adipiscing elit ut aliqum,
      purus sit amet luctus venenatis, lectus
      magna fringilla urna, porttitor" />
     
      <Notification type="info" title="Modal Window"
      message="lorem ipsum dolor sit amet,
      consectetur adipiscing elit ut aliqum,
      purus sit amet luctus venenatis, lectus
      magna fringilla urna, porttitor" />
      
      <Notification type="danger" title="Modal Window"
      message="lorem ipsum dolor sit amet,
      consectetur adipiscing elit ut aliqum,
      purus sit amet luctus venenatis, lectus
      magna fringilla urna, porttitor" />


  </main>
</template>

<script setup>

import Notification from './components/BaseNotification.vue'

</script>

<style>

main {
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: center;
  flex-direction: column;
}
</style>
