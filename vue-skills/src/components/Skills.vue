<template>
  <div class="hello">
    <div class="holder">
      <ul>
        <li v-for="(data, index) in skills" :key=index> {{ index }}. {{ data.skill }}</li>
      </ul>
    </div>

    <p v-if="skills.length > 1">I have more than one skill</p>
    <p v-else="skills.length <= 1">I have one or no skills</p>

    <div v-bind:class="{ alert: showAlert }">v-bind:[this is the attribute]="{this is the value: and this is the condition}"</div>

    <div v-bind:class="{ alert: showAlert, 'bold-text': showBold }">We can add multiple classes to this by separating the next value and expression with a comma</div>

    <div v-bind:class="classObj">This can get out of hand, so we can set an object on the data.</div>

    <div v-bind:style="{backgroundColor: bgColor, width: bgWidth, height: bgHeight }">V-bind can also be applied to style, and values can be pulls from properties stored in data</div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skills: [
        { "skill": "Learning new concepts fast" },
        { "skill": "Adaptability" },
        { "skill": "Front end developer" }
      ],
      bgColor: 'grey',
      bgWidth: '100px',
      bgHeight: '200px'
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

.alert {
  background-color: yellow;
}

.bold-text {
  font-weight: bold
}
</style>
