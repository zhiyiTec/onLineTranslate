<template>
	<div class="translateForm">
	<form class="form-inline well translateForm" v-on:submit="formSubmit">
  <div class="form-group">
    
    <input type="text" class="form-control" id="exampleInputName2" placeholder="输入翻译的内容" v-model="textToTranslate">
  </div>
  
  <select v-model="language" >
		<option value="start">点击选择语言</option>
		<option value="en">English</option>
		<option value="ru">Russia</option>
		<option value="ko">Kora</option>
		<option value="ja">Japanese</option>
  </select>
  <button type="submit" class="btn btn-default"><span class="glyphicon glyphicon-search" aria-hidden="true"></span>翻译</button>
</form>
	</div>
</template>

<script>
	import '../assets/css/bootstrap.min.css'
	import '../assets/css/bootstrap-theme.min.css'
	import '../assets/js/jquery-3.3.1.min.js'
	import '../assets/js/bootstrap.min.js'
	export default {
		name: 'translateForm',
		data() {
			return {
				textToTranslate:"",
				language:""
			}
		},
		methods:{
			formSubmit:function(e){
			if(this.language=='start'){
				this.language='en'
			}
			this.$emit("formSubmit",this.textToTranslate,this.language);//用于事件注册
			e.preventDefault();
			}
		},
		created () {
			this.language="start";
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.translateForm{
		border-radius: 10px;
		border: 1px,#ccc solid;
	}
</style>
