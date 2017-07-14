<template>
	<div class="image svg--mask">
			<svg height="0" width="0">
		    <defs>
					<clipPath :id="svgId" clipPathUnits="objectBoundingBox">
				    <path :d="nuPath" :id="svgId"></path>
					</clipPath>
		    </defs>
			</svg>
			<div class="mask" :style="{ 'clip-path': 'url(#' + svgId + ')' }">
				<slot></slot>
			</div>
	</div>
</template>

<script>
export default {
  name: 'svg-path',
  props: {
    svgPath: undefined,
    svgWidth: undefined,
    svgHeight: undefined,
    svgId: undefined
  },
  data() {
    return {
      nuPath: ''
    };
  },
  mounted() {
    this.nuPath = this.makeResponsive(
      this.svgPath,
      this.svgWidth,
      this.svgHeight
    );
  },
  methods: {
    makeResponsive(svgPath, svgWidth, svgHeight) {
			let count = -1;
			function replacer(match) {
				count++;
				if (count % 2) {
					return match / svgHeight;
				} else {
					return match / svgWidth;
				}
			}
			return svgPath.replace(/(\d+(\.\d+)?)/g, replacer);
    }
  }
};
</script>

<style lang="scss" scoped>

img { width: 100%; height: auto; display: block; }

.svg--mask { border: 1px solid red; }

</style>
