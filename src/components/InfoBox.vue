<template>
  <div class="container-fluid wrapper">
    <div class="row">
      <span> {{ firstTitle }} </span>
      <h1> {{ firstInfo }} </h1>
    </div>
    <div class="row">
      <span> {{ secondTitle }} </span>
      <h1> {{ secondInfo }} </h1>
    </div>
    <div class="row">
      <button class="btn btn-primary" type="button">
        <span>Try Some Action</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'InfoBox',
  props: {
    firstInfo: {
      type: String,
      default: ''
    },
    secondInfo: {
      type: String,
      default: ''
    },
    firstTitle: {
      type: String,
      default: ''
    },
    secondTitle: {
      type: String,
      default: ''
    }
  },
}
</script>

<style scoped lang="scss">
.wrapper {
  width: 100%;
  height: 100%;
  min-height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;

  .row {
    width: 100%;
    text-align: left;
  }
  
  .btn {
    background-color: $color1;
    border: none;
    padding: 10px;
    transition: ease .5s;
    margin-left: 0;
    
    &:focus {
      outline: 0 !important;
      box-shadow: none;
    }

    &:hover {
      background-color: $color4;
    }

    span {
      color: #000;
      font-size: 20px;
      font-weight: 700;
    }
  }
}
</style>
