<template lang="pug">
  #app
    .pictures
      img(src="./assets/IMG_1.png")
      img(src="./assets/IMG_2.png")
      img(src="./assets/IMG_3.png")
      img(src="./assets/IMG_4.png")
      img(src="./assets/IMG_5.png")
    h1 {{ msg }}
    h2 Essential Links
    ul
      li
        a(href="https://vuejs.org" target="_blank") Core Docs
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.pictures {
  position: relative;

  img {
    position: absolute;
    transition: transform 0.4s;

    transform-origin: 0 100%;
    @for $i from 1 to 6 {

        &:nth-child(#{$i}) {
           transform: rotateZ(#{$i * 15 - 45}deg);
         }
      }
  &:hover {
    transform: translateX(100px);
    z-index: 10;
   }
  }

}

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
</style>
