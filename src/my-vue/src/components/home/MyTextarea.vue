<template>
    <b-form-textarea
      id="input-1"
      v-model="text"
      :placeholder="'Enter something, maximum is ' + maximumLength + '...'"
      rows="3"
      max-rows="6"
      @keyup="textLength"
      @keydown="textLength"
      @keypress="textLength"
    ></b-form-textarea>
  </template>
   
  <script>
  export default {
    name: 'MyTextarea',
    data: () => ({
      text: ''
    }),
    props: {
      maximumLength: Number
    },
    methods: {
      textLength: function () {
        this.$emit('setTextLength', this.text.length)
      }
    }
  }
  </script>