<template>
  <div class="wrapper" :style="{'flex-direction': expand ? 'row' : 'column'}">
    <img :src="data.image" @click="emit('click')" />
    <div class="data">
			<label>Name</label>
			<span>{{data.title}}</span>
			<label>Entstehungsjahr</label>
			<span>{{year}}</span>
			<label>Technik</label>
			<span>{{data.technique}}</span>
			<label>Maße</label>
			<span>{{data.dimensions}} cm</span>
			
			<p v-if="data.description">{{data.description}}</p>
    </div>
  </div>
</template>

<script>
import { computed } from '@nuxtjs/composition-api'

export default {
	props: ["data", "expand"],
	setup({ data, expand }, { emit }) {
		const year = computed(() => parseInt(data.date.slice(0, 4)) + 1)

		return { year, emit }
	}
};
</script>

<style lang="scss" scoped>
.wrapper {
	margin: 5rem 0;
	display: flex;
	justify-content: flex-start;
	width: 100%;
	align-items: center;
  img {
		display: block;
		width: 60%;
		height: auto;
	}
  .data {
		padding: 0 0 0 10%;
		label {
			display: block;
			font-size: .7rem;
			font-weight: bold;
			color: grey;
		}
		span {
			line-height: 2.2;
			font-size: 1.2rem;
			margin-bottom: 1rem;
			display: block;
		}
  }
}
</style>