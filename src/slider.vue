<template>
<div class="mint-slider" ref="wrap">
  <div class="mint-slider-items-wrap" ref="sliders"
    @touchstart="touchStartHandle"
    @touchmove="touchMoveHandle"
    @touchend="touchEndHandle"
    @webkit-transition-end="onTransitionEnd()"
    @transitionend="onTransitionEnd()"
  >
    <slot></slot>
  </div>
  <div class="mint-slider-indicators" v-if="showIndicators && pageCount > 1">
    <div v-for="(item, index) in pageCount" :key="index" :class="{
      'mint-slider-indicator': true,
      'is-active': index === activePage
    }">{{item}}</div>
  </div>
</div>
</template>

<script>
export default {
  name: 'mt-slider',
  props: {
    perView: {
      type: Number,
      default: 1
    },
    perGroup: {
      type: Number,
      default: 1
    },
    groupFull: {
      type: Boolean,
      default: false
    },
    showIndicators: {
      type: Boolean,
      default: true
    }
  },
  data () {
    return {
      slidesPerView: this.perView, // slider容器能够同时显示的slides数量 最小值1 默认1
      // slidesPerGroup: 1, // slides的数量多少为一组 最小值1 默认1 必须整数
      slidesGroupFull: this.groupFull,
      wrap: null, // element 滚动容器
      wrapWidth: 0,
      sliders: null, // element 滚动体
      slidersWidth: 0, // 滚动体宽度 sliderWidth * itemLength
      sliderWidth: 0, // 容器宽度
      ready: false, // 数据状态标识
      itemLength: 0, // 数据长度
      maxMoveIndex: 0, // 最大滚动数量
      reInitTimer: null, // 定义计时器 初始化数据使用
      direction: null, // 滚动方向标记 left/right
      activeIndex: 0, // 当前选中的index
      isAnimation: false, // 动画中状态标记
      pageCount: 0,
      start: { // 位置标记 开始
        x: null,
        y: null
      },
      end: { // 位置标记 结束
        x: null,
        y: null
      },
      distan: { // 移动位置标记
        x: 0,
        y: 0
      },
    };
  },
  computed: {
    // slides的数量多少为一组 最小值1 默认1 必须整数
    slidesPerGroup () {
      return Math.floor(Math.min(this.perView, this.perGroup));
    },
    activePage () {
      return Math.ceil(this.activeIndex / this.slidesPerGroup);
    }
  },
  created() {
  },
  mounted () {
    this.wrap = this.$refs.wrap;
    this.sliders = this.$refs.sliders;
    this.ready = true;
    this.wrapWidth = this.$refs.wrap.offsetWidth;
    this.sliderWidth = Math.ceil(this.wrapWidth / this.slidesPerView);
    this.reInitPages();
  },
  methods: {
    sliderItemCreated() {
      if (!this.ready) return;
      clearTimeout(this.reInitTimer);
      this.reInitTimer = setTimeout(() => {
        this.reInitPages();
      }, 100);
    },
    sliderItemDestroyed() {
      if (!this.ready) return;
      clearTimeout(this.reInitTimer);
      this.reInitTimer = setTimeout(() => {
        this.reInitPages();
      }, 100);
    },
    // 初始化数据
    reInitPages () {
      const children = this.$children;
      const _length = children.length || 0;
      this.itemLength = _length;
      this.pageCount = Math.ceil((this.itemLength - this.slidesPerView) / this.slidesPerGroup + 1);
      if (this.slidesGroupFull) {
        this.maxMoveIndex = this.slidesPerView * (this.pageCount - 1);
      } else {
        this.maxMoveIndex = _length - this.slidesPerView;
      }      
      children.forEach(child => {
        child.$el.style['width'] = `${this.sliderWidth}px`;
      });
      this.setSlidersStyle();
    },
    /**
    *根据索引计算出样式
    */
    setSlidersStyle () {
      let pageLength = this.slidesGroupFull ? this.pageCount * this.slidesPerGroup : this.itemLength;
      this.slidersWidth = Math.ceil(pageLength * this.sliderWidth);
      this.sliders.style['transform'] = 'translateX(0)';
      this.sliders.style['transition'] = 'none';
      this.sliders.style['width'] = `${this.slidersWidth}px`;
    },
    /**
     * touchstart handle
     */
    touchStartHandle (event) {
      event.preventDefault();
      let touch = event.touches[0];
      this.start.x = touch.pageX;
      this.start.y = touch.pageY;
    },
    /**
     * touchmove handle
     */
    touchMoveHandle (event) {
      let touch = event.touches[0];
      this.isAnimation = true;
      this.end.x = touch.pageX;
      this.end.y = touch.pageY;
      this.distan.x = this.end.x - this.start.x;
      this.distan.y = this.end.y - this.start.y;
      let _sliderWidth = this.distan.x - this.sliderWidth * this.activeIndex;
      if (_sliderWidth > 0) {
        _sliderWidth = _sliderWidth * 0.3;
      }
      if (_sliderWidth < this.wrapWidth - this.slidersWidth) {
        _sliderWidth = 
          this.wrapWidth - this.slidersWidth + 
          ((this.maxMoveIndex - this.activeIndex) * this.sliderWidth + this.distan.x) * 0.3;
      }
      this.sliders.style['transform'] = 'translateX(' + _sliderWidth + 'px)';
      this.sliders.style['transition'] = 'none';
    },
    /**
     * touchend handle
     */
    touchEndHandle (event) {
      let touch = event.changedTouches[0];
      this.isAnimation = true;
      this.end.x = touch.pageX;
      this.end.y = touch.pageY;
      this.distan.x = this.end.x - this.start.x;
      this.distan.y = this.end.y - this.start.y;

      this.getTouchDirection(this.distan.x, this.distan.y);
      const _moveLength = Math.ceil(Math.abs(this.distan.x / this.sliderWidth));
      const _slidesPerGroup = Math.max(this.slidesPerGroup, _moveLength);
      if (this.direction === 'left') {
        this.activeIndex = this.activeIndex + _slidesPerGroup;
      } else if (this.direction === 'right') {
        this.activeIndex = this.activeIndex - _slidesPerGroup;
      }
      if (this.activeIndex < 0) {
        this.activeIndex = 0;
      }
      if (this.activeIndex > this.maxMoveIndex) {
        this.activeIndex = this.maxMoveIndex;
      }
      this.sliders.style['transform'] = `translateX(${-this.activeIndex * this.sliderWidth}px)`;
      this.sliders.style['transition'] = 'transform .5s ease';
      this.distan.x = 0;
      this.distan.y = 0;
      this.direction = null;
    },
    onTransitionEnd () {
      this.isAnimation = false;
      this.$emit('change', this.activeIndex);
      this.$nextTick(() => {
        this.sliders.style['transition'] = 'none';
        this.sliders.style['transform'] = `translateX(${-this.activeIndex * this.sliderWidth}px)`;
      });
    },
    /**
     * getAngle 计算角度
     */
    getAngle (x, y) {
      return Math.atan2(y, x) * 180 / Math.PI;
    },
    /**
     * getTouchDirection 获取滑动方向
     */
    getTouchDirection (x, y) {
      if (Math.abs(x) > 20) {
        let angle = this.getAngle(x, y);
        if (angle >= -45 && angle <= 45) { // 向右
          this.direction = 'right';
        } else if ((angle >= 135 && angle <= 180) || (angle >= -180 && angle < -135)) { // 向左
          this.direction = 'left';
        }
      }
    },
  }
};
</script>
<style lang="stylus" scoped>
.mint-slider
  width 100%
  overflow hidden
  .mint-slider-items-wrap
    overflow hidden
    .mint-slider-item
      float left
      min-height 10px
  .mint-slider-indicators
    width 100%
    padding 8px 0
    text-align center
    font-size 0
    line-height 0
    .mint-slider-indicator
      display inline-block
      text-indent -9999px
      width 8px
      height 4px
      font-size 0
      line-height 0
      background #d9d9e7
      &.is-active
        background #6282fb
      &:first-child
        border-radius 3px 0 0 3px
      &:last-child
        border-radius 0 3px 3px 0
</style>
