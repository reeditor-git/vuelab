<template>
    <div>
      <b-button
         type="submit"
         variant="primary"
         :disabled="isDisabled" 
      >
       Button
       </b-button>
    </div>
  </template>
  <script>
  export default {
    name: 'MyButton',
    props: {
      isDisabled: Boolean
    }
  }
  </script>