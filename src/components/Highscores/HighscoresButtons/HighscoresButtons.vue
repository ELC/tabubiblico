<template>
  <div class="highscores-buttons">

    <button type="button" class="btn" id="highscores-back-to-menu" v-on:click="showMenu">
      Volver al Menú
    </button>
    &nbsp;
    <button type="button" class="btn btn--fail" id="highscores-delete-highscores"
      v-if="hasHighscores" v-on:click="deleteHighscores">
      Borrar Puntuaciones
    </button>

  </div>
</template>

<script>
  export default {
    name: 'HighscoresButtons',
    props: ['hasHighscores'],
    methods: {
      deleteHighscores () {
        this.$store.commit('deleteHighscores');
      },
      showMenu () {
        this.$store.commit('showMenu');
      }
    }
  };
</script>
