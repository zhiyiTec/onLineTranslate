<template>
	<div id="app">
		<h1 style="font-family: STXingkai;">在线翻译</h1>
		<h5 class="text-muted">简单/易用/便捷</h5>
		<TranslateForm v-on:formSubmit="formSubmit"></TranslateForm>
		<TranslateOutput v-text="translatedText"></TranslateOutput>
	</div>
</template>

<script>
	import HelloWorld from './components/HelloWorld'
	import TranslateForm from './components/TranslateForm'
	import TranslateOutput from './components/TranslateOutput'
	export default {
		name: 'App',
		components: {
			HelloWorld,
			TranslateForm,
			TranslateOutput
		},
		data() {
			return {
				translatedText: "",
			}
		},
		methods: {
			formSubmit: function(text,language) {
				this.$http.get(
					"https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181111T115634Z.a26b275c72ad9f9f.9b5c1e7d6c8fd92b6f269d7fa2843a8c4a07f1be&lang="+language+"&text=" +
					text).then(function(response) {
					console.log(response.body.text[0]);
					this.translatedText = response.body.text[0];
				})
			}
		}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
