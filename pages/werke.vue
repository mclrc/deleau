<template>
  <div class="wrapper">
    <FancyImage
      src="/images/01_intro.png"
      width="100%"
      height="20vmin"
      label="Werke"
    ></FancyImage>
    <div class="content">
      <Painting
        v-for="painting in paintings"
        @click="enlargePainting(painting)"
        :expand="true"
        :key="painting.slug"
        :data="painting"
      />
    </div>
    <div
      v-show="enlargedPainting"
      class="overlay"
      @click="enlargedPainting = null"
    >
      <div class="painting" :style="{
				backgroundImage: `url(${enlargedPainting && enlargedPainting.image})`
			}"></div>
			<span>Zum verlassen erneut klicken</span>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    return {
      paintings: await $content("bilder").fetch(),
    };
  },
  data() {
    return {
      enlargedPainting: null,
    };
  },
  methods: {
    enlargePainting(painting) {
      this.enlargedPainting = painting;
    },
  },
};
</script>

<style lang="scss" scoped>
.content {
  max-width: 1000px !important;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
	width: calc(100vw - (100vw - 100%));
  height: 100vh;
  z-index: 10;
	background-color: rgba(0, 0, 0, 0.9);
	
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	.painting {
		width: 90%;
		height: 90%;
		background-size: contain;
		background-repeat: no-repeat;
		background-position: center;
	}
	span {
		color: #999;
		line-height: 3;
		font-weight: lighter;
	}
}
</style>