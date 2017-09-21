<template>
  <div class="hello">
    <div id=top>
    <h1>{{ msg }}</h1><br>
    <textarea v-model="text" placeholder="Fang einfach an zu schreiben!"></textarea>
    </div>    
    <div class="txt"><p  v-if="text.length > 0"><i>HTML-Text</i></p><p >{{ hyText }}</p></div>
   <div class="txt"> <p  v-if="text.length > 0"><i>HTML-Vorschau</i></p><div v-html='hyText'></div></div>
    
  </div>
</template>

<script>
import hyphe from '../assets/hyphe-lib-ger'
export default {
  name: 'hello',
  data () {
    return {
      msg: '\{\{ hyphenate mich \}\}', 
      text: '',
      hyText: this.text
    }
  },
  updated: function() {

},
  methods: {
  },
  watch: {
    text: function() {
      hyphe.hyphe('HTML', this.text, (h) => {
        this.hyText = h;
      })
    } 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
textarea {
  height: 20rem;
  width: 50rem
}

.txt {
  padding: 1%;
  float: left;
  text-align: justify;
  width: 45%;
  margin: 0 auto;
}

#top {
  margin-bottom: 3rem;
}
</style>
