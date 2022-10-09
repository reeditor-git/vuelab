<template>
  <div class="hello">
    <b-container>
      <b-form class="text-justify">
        <myFormLable 
          :textLength="textLength" 
          :maximumLength="maximumLength" 
          :lableClass="lableClass" 
        />
        <myTextarea :maximumLength="maximumLength" @setTextLength="setTextLength"/>
        <myButton :isDisabled="maximumAchieved"/>
      </b-form>
    </b-container>
  </div>
</template>

<script>
import MyFormLable from '@/components/home/MyFormLable.vue'
import MyButton from '@/components/home/MyButton.vue'
import MyTextarea from '@/components/home/MyTextarea.vue'

export default {
  name: 'HelloWorld',
  data: () => ({
    maximumLength: 40,
    warningLength: 30,
    textLength: 0
  }),
  components: {
    MyFormLable,
    MyButton,
    MyTextarea
  },
  computed: {
    lableClass: function () {
      var lableClass = 'success'
      if (this.textLength >= this.maximumLength) {
        lableClass = 'danger'
      } else if (this.textLength >= this.warningLength) {
        lableClass = 'warning'
      }
      return lableClass
    },
    maximumAchieved: function () {
      return (this.textLength >= this.maximumLength)
    }
  },
  methods: {
    setTextLength (textLength) {
    this.textLength = textLength
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>