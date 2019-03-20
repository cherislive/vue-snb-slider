<template>
  <div class="mint-slider-item" @click.stop="sliderItemClickHandle">
    <slot></slot>
  </div>
</template>
<script>
export default {
  name: 'mt-slider-item',
  props: {
    item: {
      type: Object,
      default: () => {
        return {};
      }
    },
  },
  data () {
    return {
    };
  },
  mounted () {
    this.$parent && this.$parent.sliderItemCreated(this);
  },
  destroyed () {
    this.$parent && this.$parent.sliderItemDestroyed(this);
  },
  methods: {
    sliderItemClickHandle () {
      this.$emit('sliderItemOnClick', this.item);
    }
  }
};
</script>
<style lang="stylus" scoped>
</style>
