<!-- HTML -->
<template>
	<h1>{{ txt }}</h1>
	<!-- Gallery -->
	<div class="galleryContainer">
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
	<hr>
	<!-- To Do list -->
	<div class="todoContainer">
		<div class="todo" v-for="item in todoObject" :key="item">
			<h3>{{ item.id }}:</h3>
			<input type="checkbox" v-model="item.completed">
			<h3>{{ item.title }}</h3>
		</div>
	</div>
</template>

<!-- JavaScript -->
<script>
	import $ from 'jquery'; //import jquery

	export default {
		name: 'Page',
		props: {
			txt: String
		},
		data() {
			return {
				url: 'https://jsonplaceholder.typicode.com',
				galleryUrl: '/albums/1/photos',
				todoUrl: '/users/1/todos',
				galleryObject: [],
				todoObject: [],
				index: 0
			};
		},
		created() {
			//API get for gallery
			$.get(this.url + this.galleryUrl, (response) => {
				this.galleryObject = response;
			});
			//API get for to do list
			$.get(this.url + this.todoUrl, (response) => {
				this.todoObject = response;
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
	/* Gallery */
	.galleryContainer {
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

	.arrLeft{
		transform: rotate(90deg);
	}

	.arrRight{
		transform: rotate(-90deg);
	}

	/* To Do List */
	.todoContainer {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		width: 800px;
		margin: auto;
	}

	.todo {
		display: flex;
	}

	input {
		margin-left: 20px;
	}
</style>