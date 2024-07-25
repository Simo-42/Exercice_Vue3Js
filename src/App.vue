<template>
  <div class="side-bar">
    <div class="notifications-container">
      <Notification 
        v-for="(notification, index) in notifications" 
        :key="notification.id"
        :index="index"
        :type="notification.type"
        :title="notification.title"
        :message="notification.message"
        @close="remove_notification"
      />
    </div>
    <p>{{ notifications.length }}</p>
  </div>

  <button class="add-notification-btn" @click="add_notification">Add Notification</button>
</template>

<script setup>
import { ref } from 'vue';
import Notification from './components/BaseNotification.vue';
import './assets/styles/notification.css';

const notifications = ref([]);
let nextId = 1;

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
];

function rand(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

const remove_notification = (index) => {
  notifications.value.splice(index, 1);
};

const add_notification = () => {
  if (notifications.value.length >= 5) {
    notifications.value.shift();
  }

  const index = rand(0, availableNotifications.length - 1); // Ajout d'une notification random
  const newNotification = {
    type: availableNotifications[index].type,
    title: availableNotifications[index].title,
    message: availableNotifications[index].message,
    id: nextId++
  };  
  notifications.value.push(newNotification);
};

</script>

<style>

</style>
