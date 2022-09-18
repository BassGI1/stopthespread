<script>
  import SinglePlayer from './components/SinglePlayer.vue';
  export default {
    name: "App",
    data() {
        return {
            render: "Menu"
        };
    },
    components: { SinglePlayer }
}
</script>

<template>
    <div class="app">
      <!-- start of menu -->
        <div class="banner" v-if="render === 'Menu'">
          <img src="/Banner.png" alt="Banner Image" style="width: 70vw;" class="banneranimation">
        </div>
        <div class="buttons" v-if="render === 'Menu'">
          <div class="menubutton" @click="render = 'SinglePlayer'">
            Single Player
          </div>
          <div class="menubutton">
            Multiplayer
          </div>
          <div class="menubutton">
            How to Play
          </div>
          <div class="menubutton">
            About
          </div>
        </div>
        <!-- end of menu -->
        <!-- start of single player -->
        <div v-if="render === 'SinglePlayer'">
          <SinglePlayer />
        </div>
    </div>
</template>

<style scoped>
  .app{
    min-width: 100vw;
    min-height: 100vh;
    overflow: hidden;
    margin: 0px;
    padding: 0px;
    background-color: rgb(130, 130, 211);
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    font-family: 'Patrick Hand', cursive;
  }
  .banner{
    width: 100vw;
    height: 40vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .banneranimation{
    animation: banneranimation 3s forwards cubic-bezier(1, 0.18, 0.2, 1.05);
  }
  @keyframes banneranimation{
    0%{
      transform: translateX(-100vw);
    }
  }
  .buttons{
    display: flex;
    width: 50vw;
    justify-content: center;
    flex-wrap: wrap;
    animation: buttons 5s forwards;
  }
  @keyframes buttons{
    0%{
      opacity: 0%;
    }
  }
  .menubutton{
    margin: 2vw;
    width: 20vw;
    height: 10vh;
    background-color: rgb(95, 95, 240);
    display: flex;
    justify-content: center;
    align-items: center;
    color: rgb(255, 250, 250);
    border-radius: 2vh;
    font-size: x-large;
    cursor: pointer;
  }
</style>