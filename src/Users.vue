<template>
	<div>
	<h1>用户页面</h1>
	<p>用户id是: {{ $route.params.teamId }}</p>
	<button @click="goHome">回首页</button>
	</div>
</template>

<script>
	export default{
		watch:{
			'$route'(to,from){
				alert(to.params.teamId);
			}
		},
		created(){
        	alert(this.$route.params.teamId);
      	},
      	methods:{
      		goHome(){
      			this.$router.push('/');
      		}
      	}
	}

</script>