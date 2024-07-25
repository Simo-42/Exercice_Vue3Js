<template>
	<div v-if="visible" :style="config.style" class="notification"> <!-- visible gere la fermeture de la modale -->
		<div class="icon-and-title">
			<img :src="config.icon" alt="icon" class="icon" />
			<h2 class="title">{{ title }}</h2>
		</div>
		<p class="message">{{ message }}</p>
		<button @click="close" class="close-btn">X</button>
	</div>
</template>


<script setup>
import { defineProps, ref , defineEmits } from 'vue'
import '../assets/styles/notification.css'

import WarningIcone from '../assets/icons/Warning.svg'
import SuccessIcone from '../assets/icons/CheckCircle.svg'
import InfoIcone from '../assets/icons/Info.svg'
import DangerIcone from '../assets/icons/Danger.svg'

 const configurations = { // config de chaque predefini 
	'warning' : {
		icon: WarningIcone,
		style: {
			backgroundColor: '#F7F2E4',
			color: '#BEAD86',
		},
	},
	'success' : {
		icon: SuccessIcone,
		style: {
			backgroundColor: '#E4F7E8',
			color: '#89B291',
		},
	},
	'info' : {
		icon: InfoIcone,
		style: {
			backgroundColor: '#E4E9F7',
			color: '#96A8D8',
		},
	},
	'danger' : {
		icon: DangerIcone,
		style: {
			backgroundColor: '#F7E4E4',
			color: '#D29393',
		},
	},
}

const props = defineProps({ // argument de la notification
	type : {
		type: String,
		required: true
	},
	title: {
		type: String,
		required: true
	},

	message: {
		type: String,
		required: true
	},
	index : {
		type: Number,
		required: true
	},
})

const emit = defineEmits(['close'])  // Permettre de comuniquer avec le parent
const config = configurations[props.type]
const visible = ref(true)

function close ()
{
	emit('close', props.index) // envoie l'index au parent
	visible.value = false
	// console.log('props.index', props.index)
}
// console.log(config)

</script>

<style scoped>

</style>
