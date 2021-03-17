<!-- HTML -->
<template>
	{{ msg }}
	<div class="container">
		<div class="left">
			<img class="arrLeft" @click="prev()" src="../assets/icons/arrow.png" alt="Arrow Left">
		</div>
		<div>
			<h1>{{ galleryObject[index].id }}</h1>
			<img :src="galleryObject[index].url" alt="Picture 600 x 600">
			<h1 class="title">{{ galleryObject[index].title }}</h1>
		</div>
		<div class="right">
			<img class="arrRight" @click="next()" src="../assets/icons/arrow.png" alt="Arrow Right">
		</div>
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
				index: 0
			};
		},
		created() {
			$.get(this.url + this.galleryUrl, (response) => {
				this.galleryObject = response;
			});
		},
		methods: {
			prev() {
				if (this.index > 0) {
					this.index --;
				} else {
					this.index = 49;
				}
			},
			next() {
				if (this.index < 49) {
					this.index ++;
				} else {
					this.index = 0;
				}
			}
		}
	};
</script>

<!-- CSS -->
<style scoped>
	.arrLeft{
		transform: rotate(90deg);
	}

	.arrRight{
		transform: rotate(-90deg);
	}

	.container {
		display: flex;
		justify-content: center;
	}

	.title {
		max-width: 600px;
	}

	.left {
		margin-top: 330px;
	}

	.right {
		margin-top: 330px;
	}
</style>