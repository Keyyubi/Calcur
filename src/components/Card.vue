<template>
  <div class="container card">
    <div class="row">
      <div class="col-lg-8 col-md-8 col-xs-12">
        <InputSlider 
          title="Salary?"
          prepend="$"
          append="k"
          :min="1"
          :max="120"
          :step="0.5"
          @changed="handleSalary"
        />
        <InputSlider 
          title="People?"
          :max="10"
          @changed="handlePeople"
        />
        <InputSlider
          title="Avarage speed?"
          :max="25"
          @changed="handleSpeed"
        />
      </div>
      <div class="col-lg-4 col-md-4 col-xs-12 info-wrapper">
        <InfoBox
          :firstInfo="hours"
          :secondInfo="money"
          firstTitle="Hours Saved"
          secondTitle="Money Saved"
        />
      </div>
    </div>
  </div>
</template>

<script>
import InfoBox from './InfoBox.vue';
import InputSlider from './InputSlider.vue';
export default {
  components: { InputSlider, InfoBox },
  name: 'Card',
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
      salary: 22,
      first: 1,
      second: 1,
      hours: ' - ',
    }
  },
  computed: {
    money () {
      const result = this.salary / 10 * (this.first + this.second)
      return new Intl.NumberFormat('en-EN', { style: 'currency', currency: 'USD' }).format(result)
    }
  },
  methods: {
    handleSalary (val) {
      this.salary = val
    },
    handlePeople (val) {
      val = val || 1
      this.first = val
      this.hours = '' + (24 * (this.first + this.second))
    },
    handleSpeed (val) {
      val = val || 1
      this.second = val
      this.hours = '' + (24 * (this.first + this.second))
    }
  },
}
</script>

<style scoped lang="scss">
.card {
  padding: 10px;
  background-color: $light-grey;
  border: none;
  margin: 20px 0;

  .info-wrapper {
    background-color: #fff;
    padding: 30px 10px;
    margin: -20px 0;
    border: 2px solid $color1;
    border-radius: 15px;

    @media only screen and (max-width: 400px) {
      width: 90%;
      margin: 20px;
    }
  }
}
</style>
