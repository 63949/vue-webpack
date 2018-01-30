<template>
	<div>
		<!-- <h1>好消息!</h1> -->
		<h1>Message本身的message: {{ message }}</h1> 
		<app-input :msg="message" @messageChanged="message = $event"></app-input>
	</div>
	
</template>

<script>
	import Input from './Input.vue';

	export default{

		data(){
			return {
				message: '好消息'
			} 
		},
		components:{
			'app-input':Input
		}
	}
</script>