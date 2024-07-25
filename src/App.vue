<template>
  <div class="side-bar">
    <div class="notifications-container">
      <Notification 
        v-for="(notification, index) in notifications" 
        :key="index"
        :type="notification.type"
        :title="notification.title"
        :message="notification.message"
      />
    </div>
  </div>
  
  <button class="add-notification-btn" @click="add_notification">Add Notification</button>
</template>

<script setup>
import { ref } from 'vue'
import Notification from './components/BaseNotification.vue'
import './assets/styles/notification.css'


const notifications = ref([])

const availableNotifications = [
  {
    type: 'warning',
    title: 'Warning Notification',
    message: 'lorem ipsum dolor sit amet, consectetur adipiscing elit ut aliqum, purus sit amet luctus venenatis, lectus magna fringilla urna, porttitor'
  },
  {
    type: 'info',
    title: 'Info Notification',
    message: 'lorem ipsum dolor sit amet, consectetur adipiscing elit ut aliqum, purus sit amet luctus venenatis, lectus magna fringilla urna, porttitor'
  },
  {
    type: 'success',
    title: 'Success Notification',
    message: 'lorem ipsum dolor sit amet, consectetur adipiscing elit ut aliqum, purus sit amet luctus venenatis, lectus magna fringilla urna, porttitor'
  },
  {
    type: 'danger',
    title: 'Danger Notification',
    message: 'lorem ipsum dolor sit amet, consectetur adipiscing elit ut aliqum, purus sit amet luctus venenatis, lectus magna fringilla urna, porttitor'
  }
]

const add_notification = () => { // fonction app lors du click sur le bouton add notification
  const randomIndex = Math.floor(Math.random() * availableNotifications.length) 
  notifications.value.push(availableNotifications[randomIndex])
}

</script>

<style>

</style>
