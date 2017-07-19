<template lang="pug">
  #app
    .pictures(@mouseout="loseHover")
      img(@click="addActive" src="./assets/IMG_2.png")
      img(@click="addActive" src="./assets/IMG_3.png")
      img(@click="addActive" src="./assets/IMG_4.png")
      img(@click="addActive" src="./assets/IMG_5.png")

</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      isActive: false
    }
  },
  methods: {
      addActive: function(evt) {
        this.isActive = !this.isActive;
        [...document.querySelector('.pictures').childNodes].forEach( i => i.classList.remove('active'));
          if(this.isActive) {
            evt.target.classList.add('active');
          }
      },
      loseHover: function(evt) {
        this.isActive = false;
        [...document.querySelector('.pictures').childNodes].forEach( i => i.classList.remove('active'));
      }

  }
}
</script>

<style lang="scss">
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.pictures {
  width: 500px;
  height: 500px;
  display: flex;
  position: relative;

  &:hover {
    img {
      @for $i from 1 to 6 {
        &:nth-child(#{$i}) {
          transform: rotateZ(#{$i * 15 - 30}deg) scale(0.5);

        &:hover {
           transform: rotateZ(#{$i * 15 - 30}deg) translate(20px, -40px) scale(0.5);
         }
        }
      }

      &.active:hover{
         transform: scale(1);
         z-index: 10;
       }
    }
   }

  img {
    position: absolute;
    transition: transform 0.4s;
    transform: scale(0.5);
    transform-origin: 50% 100%;
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
