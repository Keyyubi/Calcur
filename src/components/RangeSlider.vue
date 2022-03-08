<template>
  <div class="container">
    <div class="info-row">
      <h3>Title</h3>
      <span>{{value}}</span>
    </div>
    <div ref="slider" class="range-wrapper">
      <div class="range" :style="'width:' + value + '%'"></div>
      <div class="thumb"
        @mousedown="dragStart"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RangeSlider',
  props: {
    min: {
      type: Number,
      default: 0
    },
    max: {
      type: Number,
      default: 100
    },
    step: {
      type: Number,
      default: 1,
    }
  },
  data () {
    return {
      width: null,
      offset: 0,
      value: 50,
      dragging: false,
      start: 0,
      end: 0,
    }
  },
  mounted () {
    this.$nextTick(function() {
      this.width = this.$refs.slider.offsetWidth;
      this.offset = this.$refs.slider.getBoundingClientRect().left;
      this.bindListener();
    })
  },
  methods: {
    bindListener () {
      document.addEventListener("mousemove", this.handleDrag);
      document.addEventListener("mouseup", this.dragEnd);
    },
    getPosition (ev) {
      return ev.clientX - this.offset;
    },
    setPosition (pos) {
      this.position = pos - this.step;
    },
    dragStart (e) {
      this.dragging = true
      this.start = e.clientX
    },
    dragEnd () {
      this.dragging = false
    },
    handleDrag (e) {
      if (!this.dragging) return;
      const { left, right, width } = this.$refs.slider.getBoundingClientRect()

      if (e.clientX > left && e.clientX < right) {
        if (this.start < e.clientX) {
          this.value += Math.round(((e.clientX - this.start) * 100) / width)
        } else {
          this.value -= Math.round(((this.start - e.clientX) * 100) / width)
        }
      } else if (e.clientX <= left) {
        this.value = this.min
      } else if (e.clientX >= right) {
        this.value = this.max
      }

      this.start = e.clientX
    }
  },
}
</script>

<style scoped lang="scss">
.info-row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 5px;
}

.range-wrapper {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  cursor: pointer;
  width: 100%;
  height: 8px;
  background-color: $light-grey;
  border-radius: 15px;

  .range {
    z-index: 1;
    background-color: $color1;
    height: 8px;
    margin-right: -5px;
    border-radius: 15px;
  }
  
  .progress {
    z-index: 1;
    background-color: $light-grey;
    height: 8px;
    margin-left: -5px;
    border-radius: 15px;
  }

  .thumb {
    z-index: 11;
    width: 16px;
    height: 16px;
    background-color: #fff;
    border-radius: 50%;
    box-shadow: 0px 0px 10px -2px $shadow-color;
    transition: ease-in .3s;

    &:hover {
      background-color: $color2;
    }
  }
}
</style>
