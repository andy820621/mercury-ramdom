<script setup lang="ts">
import { ref } from "vue";
const startNumber = ref(75);
const endNumber = ref(100);
const count = ref(1);
const randomNumbers = ref<number[]>([]);

const generateRandomNumbers = () => {
	randomNumbers.value = [];

	for (let i = 0; i < count.value; i++) {
		const randomNumber = Math.floor(
			Math.random() * (endNumber.value - startNumber.value + 1) +
				startNumber.value
		);
		randomNumbers.value.push(randomNumber);
	}
};
</script>

<template>
	<header>
		<img alt="Vue logo" class="logo" src="./assets/icon.png" />
		<h1>水星防火工程</h1>
	</header>

	<main class="main">
		<div class="random-box">
			<h2>亂數生成器</h2>
			<div class="startToEnd">
				<div class="inputBox">
					<label for="start">起始數字: </label>
					<input id="start" type="number" v-model="startNumber" />
				</div>
				<div class="inputBox">
					<label for="end">結束數字: </label>
					<input id="end" type="number" v-model="endNumber" />
				</div>
			</div>
			<div class="inputBox">
				<label for="count">需要產出的數字個數: </label>
				<input id="count" type="number" v-model="count" />
			</div>
			<button class="btn" @click.prevent="generateRandomNumbers">
				生成亂數
			</button>
		</div>

		<div class="content" v-if="randomNumbers.length > 0">
			<h2>隨機數字:</h2>
			<ul>
				<li v-for="number in randomNumbers" :key="number">{{ number }}</li>
			</ul>
		</div>
	</main>
</template>

<style scoped lang="scss">
header {
	display: flex;
}

.logo {
	display: block;
	margin-left: 1rem;
	margin-right: 1rem;
	width: 2.4rem;
	height: 2.4rem;
}

h1 {
	font-size: 1.5rem;
	margin: 0;
}
.content,
.random-box {
	margin: 0 auto;
	display: flex;
	flex-direction: column;
	width: 800px;
	align-items: center;
	gap: 1rem;
	font-size: 1.2rem;
}

.random-box {
	margin-top: 1rem;
	label {
		display: inline-block;
		width: 190px;
		text-align: left;
		margin-right: 10px;
	}

	input {
		padding: 5px;
		font-size: 16px;
	}
	.startToEnd {
		display: grid;
		gap: 1rem;
	}
	.btn {
		padding: 10px 20px;
		font-size: 18px;
		background-color: #007bff;
		color: #fff;
		border: none;
		cursor: pointer;
		margin-top: 1rem;
		border-radius: 5px;
		&:hover {
			background-color: #0056b3;
		}
	}
}

ul {
	list-style-type: none;
	padding: 0;
}

li {
	margin: 5px 0;
	font-size: 1.5rem;
}

/* @media (min-width: 1024px) {
} */
</style>
