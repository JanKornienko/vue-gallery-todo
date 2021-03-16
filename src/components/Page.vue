<template>
	<div class="container">
		<div class="box">
			{{ msg }}
		</div>
	</div>
</template>

<script>
	import $ from 'jquery';

	export default {
		name: 'Page',
		props: {
			msg: String
		},
		data() {
			return {
				url: 'https://jsonplaceholder.typicode.com',
				galleryUrl: '/albums/1/photos',
				todoUrl: '/users/1/todos',
				galleryObject: {},
				todoObject: {}
			};
		},
		created() {
			$.get(this.url + this.galleryUrl, (response) => {
				this.galleryObject = response;
				console.log(response);
			})
		}
	};
</script>

<style scoped>
</style>