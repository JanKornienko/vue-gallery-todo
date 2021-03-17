<!-- HTML -->
<template>
	{{ msg }}
	<div v-for="picture in galleryObject" :key="picture">
		<img :src="picture.url" alt="Picture 600 x 600">
	</div>
</template>

<!-- JavaScript -->
<script>
	import $ from 'jquery'; //import jquery

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
				galleryObject: [],
				todoObject: []
			};
		},
		created() {
			$.get(this.url + this.galleryUrl, (response) => {
				this.galleryObject = response;
				console.log(this.galleryObject);
			});
		},
		methods() {
		}
	};
</script>

<!-- CSS -->
<style scoped>
</style>