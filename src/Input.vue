<template>
	<div>
		<p>接受父模块来的属性：{{ msg }}</p>
		<!-- <input type="text" v-model="message"></input> -->
		<!-- <input type="text" :value="msg"></input> -->
		<input type="text" :value="msg" @input="changeMessage"></input>
		<p>{{message}}</p>
	</div>
</template>

<script>
	export default{
		props:['msg'],
		data(){
			return {
				message:''
			}
		},
		methods:{
			changeMessage(){
				this.message = event.target.value;
				this.$emit('messageChanged',this.message);
			}
		}
	}
</script>