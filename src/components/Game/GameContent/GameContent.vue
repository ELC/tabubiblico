<template>
  <div class="game-content">

    <div class="game-content__endpanel" v-if="displayEndpanel">
      <div class="game-content__endpanel-content">
        <div class="game-content__endpanel-header">
          Partida Terminada!
        </div>
        <br>
        <button type="button" class="btn" id="game-show-highscore" v-on:click="showHighscores">
          Ver Puntuaciones
        </button>
        <button type="button" class="btn" id="game-back-to-menu" v-on:click="showMenu">
          Volver al Menú
        </button>
      </div>
    </div>

    <div class="game-content__keyword" v-if="!displayEndpanel">
      {{ getKeyword }}
    </div>

    <div class="game-content__buzzwords" v-if="displayBuzzwords">
      <div class="game-content__buzzword" v-for="buzzword in getBuzzwords">{{ buzzword }}</div>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'GameContent',
    computed: {
      getKeyword () {
        this.theKeyword = this.$store.state.keyword;
        return this.theKeyword;
      },
      getBuzzwords () {
        return this.$store.state.buzzwords;
      },
      gameStarted () {
        return this.$store.state.gameStarted;
      },
      displayEndpanel () {
        return !(this.$store.state.gameStarted || this.$store.state.gameCountdown);
      },
      displayBuzzwords () {
        return this.$store.state.buzzwords.length > 0 && this.$store.state.gameStarted;
      }
    },
    methods: {
      showHighscores () {
        this.$store.commit('showHighscores', true);
      },
      showMenu () {
        this.$store.commit('showMenu');
      }
    }
  };
</script>
