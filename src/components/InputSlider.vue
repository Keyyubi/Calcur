<template>
  <div class="container my-3">
    <div class="info-row">
      <h4>{{ title }}</h4>
      <span>{{ prepend + value + append }}</span>
    </div>
    <div class="range-wrapper">
      <input 
        v-model="value"
        class="slider slider-progress"
        type="range"
        :min="min"
        :max="max"
        :step="step"
        @input="setPath"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'InputSlider',
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
      default: 1
    },
    prepend: {
      type: String,
      default: ''
    },
    append: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      value: Math.round(this.max / 2),
    }
  },
  mounted () {
    this.setPath()
  },
  methods: {
    setPath () {
      for (let e of document.querySelectorAll('input[type="range"].slider')) {
        e.style.setProperty('--value', e.value);
        e.style.setProperty('--min', e.min == '' ? '0' : e.min);
        e.style.setProperty('--max', e.max == '' ? '100' : e.max);
        e.addEventListener('input', () => e.style.setProperty('--value', e.value));
      }

      this.$emit('changed', this.value)
    }
  }
}
</script>

<style scoped lang="scss">
.info-row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 5px;

  span {
    font-size: 22px;
    font-weight: 800;
  }
}

.range-wrapper {
  cursor: pointer;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  width: 100%;
  height: 8px;
  background-color: $grey;
  border-radius: 15px;
}

/*generated with Input range slider CSS style generator (version 20211225)
https://toughengineer.github.io/demo/slider-styler*/
input[type=range].slider {
  cursor: pointer;
  width: 100%;
  height: 8px;
  -webkit-appearance: none;
}

/*progress support*/
input[type=range].slider.slider-progress {
  --range: calc(var(--max) - var(--min));
  --ratio: calc((var(--value) - var(--min)) / var(--range));
  --sx: calc(0.5 * 22px + var(--ratio) * (100% - 22px));
}

input[type=range].slider:focus {
  outline: none;
}

/*webkit*/
input[type=range].slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 22px;
  height: 22px;
  border-radius: 16px;
  background: #FFFFFF;
  border: none;
  box-shadow: 0 0 2px black;
  margin-top: calc(max((16px - 1px - 1px) * 0.5,0px) - 22px * 0.5);
}

input[type=range].slider::-webkit-slider-runnable-track {
  height: 16px;
  border-radius: 8px;
  background: $grey;
  box-shadow: none;
}

input[type=range].slider::-webkit-slider-thumb:hover {
  background: $color2;
}

input[type=range].slider::-webkit-slider-thumb:active {
  background: $color2;
}

input[type=range].slider.slider-progress::-webkit-slider-runnable-track {
  background: linear-gradient($color1,$color1) 0/var(--sx) 100% no-repeat, $grey;
}

input[type=range].slider.slider-progress:hover::-webkit-slider-runnable-track {
  background: linear-gradient($color4,$color4) 0/var(--sx) 100% no-repeat, $grey;
}

/*mozilla*/
input[type=range].slider::-moz-range-thumb {
  width: 22px;
  height: 22px;
  border-radius: 16px;
  background: #FFFFFF;
  border: none;
  box-shadow: 0 0 2px black;
}

input[type=range].slider::-moz-range-track {
  height: max(calc(16px - 1px - 1px),0px);
  border-radius: 8px;
  background: $grey;
  box-shadow: none;
}

input[type=range].slider::-moz-range-thumb:hover {
  background: $color2;
}

input[type=range].slider::-moz-range-thumb:active {
  background: $color2;
}

input[type=range].slider.slider-progress::-moz-range-track {
  background: linear-gradient($color1,$color1) 0/var(--sx) 100% no-repeat, $grey;
}

input[type=range].slider.slider-progress:hover::-moz-range-track {
  background: linear-gradient($color4,$color4) 0/var(--sx) 100% no-repeat, $grey;
}

/*ms*/
input[type=range].slider::-ms-fill-upper {
  background: transparent;
  border-color: transparent;
}

input[type=range].slider::-ms-fill-lower {
  background: transparent;
  border-color: transparent;
}

input[type=range].slider::-ms-thumb {
  width: 22px;
  height: 22px;
  border-radius: 16px;
  background: #FFFFFF;
  border: none;
  box-shadow: 0 0 2px black;
  margin-top: 0;
  box-sizing: border-box;
}

input[type=range].slider::-ms-track {
  height: 16px;
  border-radius: 8px;
  background: $grey;
  box-shadow: none;
  box-sizing: border-box;
}

input[type=range].slider::-ms-thumb:hover {
  background: $color2;
}

input[type=range].slider::-ms-thumb:active {
  background: $color2;
}

input[type=range].slider.slider-progress::-ms-fill-lower {
  height: max(calc(16px - 1px - 1px),0px);
  border-radius: 8px 0 0 8px;
  margin: -1px 0 -1px -1px;
  background: $color1;
  border-right-width: 0;
}

input[type=range].slider.slider-progress:hover::-ms-fill-lower {
  background: $color4;
}


</style>
