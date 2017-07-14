<template>
  <div id="app">

		<section class="section--full">

			<div class="section--inner">

				<div class="section--content">

					<div class="block" v-for="mask in maskData">
							<SvgPath :svgId="mask.id" :svgPath="mask.path" :svgWidth="mask.width" :svgHeight="mask.height">
								<img src="http://lorempixel.com/1200/600/cats/" alt="">
							</SvgPath>
					</div>

				</div>

			</div>

		</section>

  </div>
</template>

<script>
import SvgPath from './components/SvgPath';
import { masks } from './utils/MaskPaths.js';

export default {
  name: 'app',
  components: {
    SvgPath
  },
  data() {
    return {
      maskData: ''
    };
  },
  created() {
    this.maskData = masks;
  }
};
</script>

<style lang="scss">

.block {
	margin-bottom: 2%;
}

</style>
