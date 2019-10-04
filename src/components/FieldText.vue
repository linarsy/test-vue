<template>
  <div
    class="field-text"
    v-bind:class="classField"
  >
    <label
      for="item"
      class="field-text__label"
      v-bind:class="classLabel"
    >
      Название согласования
    </label>
    <input
      type="text"
      id="item"
      class="field-text__input"
      v-model="newItem"
      v-on:focus = "setFocus"
      v-on:blur="validate(); loseFocus();"
    >
  </div>
</template>

<script>
  export default {
    data () {
      return {
        newItem: '',
        isValid: false,
        isFocus: false,
      }
    },
    computed: {
      isFilled () {
        return this.newItem.length;
      },
      classLabel () {
        return {
          small: this.isFilled || this.isFocus,
        }
      },
      classField () {
        return {
          valid: this.isFilled && !this.isFocus && this.isValid,
          invalid: this.isFilled && !this.isFocus && !this.isValid,
        }
      },
    },
    methods: {
      setFocus () {
        return this.isFocus = true;
      },
      loseFocus () {
        return this.isFocus = false;
      },
      validate () {
        return this.isValid = this.newItem.length >= 8;
      },
    }
  }
</script>

<style lang="scss" scoped>
  @import '../variables.scss';

  .field-text {
    position: relative;
    &::before {
      content: "";
      position: absolute;
      top: 50%;
      left: 15px;
      width: 20px;
      height: 20px;
      transform: translateY(-50%);
      background: url("../assets/user.svg") 0 0 no-repeat;
    }
    &::after {
        content: "";
        position: absolute;
        top: 50%;
        right: 20px;
        width: 20px;
        height: 20px;
        transform: translateY(-50%);
        background-repeat: no-repeat;
      }
    &.valid {
      .field-text__input {
        border-color: $vue-green;
      }
      &::after {
        background-image: url("../assets/tick.svg");
      }
    }
    &.invalid {
      .field-text__input {
        border-color: $vue-red;
      }
      &::after {
        background-image: url("../assets/close.svg");
      }
    }
  }

  .field-text__label {
    position: absolute;
    top: 50%;
    left: 50px;
    transform: translateY(-40%);
    color: $vue-gray;
    font-size: 14px;
    transition: all 0.3s;
  }

  .field-text__input {
    width: 100%;
    padding: 30px 50px 13px;
    font-size: 14px;
    color: $vue-dark-gray;
    letter-spacing: 0.5px;
    border-radius: 5px;
    border: 1px solid $vue-gray;
    &:focus {
      outline: none;
    }
  }

  .small {
    top: 20px;
    left: 50px;
    transform: 0;
    font-size: 11px;
  }
</style>
