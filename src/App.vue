<template>
	<div class="container">
		<form @submit.prevent class="containerMini">
			<input
				@input="title = $event.target.value"
				v-bind:value="title"
				class="inputAdd"
				type="text" />
			<button @click="createPost" class="buttonAdd">Add</button>
		</form>
		<div class="containerGlavCard">
			<div class="containerCard" v-for="posts in post">
				<span>{{ posts.title }}</span>
				<button
					@click="() => deletePost(posts.id)"
					class="buttonDelete">
					Delete
				</button>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				post: [],
				title: '',
			}
		},
		methods: {
			createPost() {
				const newPost = {
					id: Math.random().toString(),
					title: this.title,
				}
				this.post.push(newPost)
				this.title = ''
			},
			deletePost(id) {
				this.post = this.post.filter((item) => item.id !== id)
			},
		},
	}
</script>

<style>
	body {
		margin: auto;
		padding:auto;
		display: grid;
		place-items: center;
	}
	.container {
		width: 600px;
		height: 700px;
		background-color: teal;
		border-radius: 12px;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.containerMini {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.inputAdd {
		width: 300px;
		height: 30px;
		background: none;
		border: 1px solid white;
		border-radius: 12px;
		outline: none;
		color: white;
		text-align: center;
		font-size: 20px;
		margin-top: 10px;
	}
	.buttonAdd {
		width: 120px;
		padding: 5px;
		margin-top: 10px;
		border-radius: 12px;
		background-color: black;
		font-size: 16px;
		border: 1px solid white;
		color: white;
		cursor: pointer;
	}
	.containerGlavCard {
		margin-top: 10px;
		height: 500px;
		display: flex;
		flex-direction: column;
		gap: 10px;
	}
	.containerCard {
		width: 400px;
		height: 40px;
		border: 2px solid black;
		border-radius: 12px;
		background-color: whitesmoke;
		display: flex;
		justify-content: space-around;
		align-items: center;
	}
	.buttonDelete {
		width: 100px;
		height: 30px;
		border-radius: 12px;
		color: white;
		font-size: 16px;
		background-color: rgb(151, 36, 36);
		cursor: pointer;
	}
	.buttonDelete:hover {
		background-color: red;
	}
</style>
