<template lang="pug">
    #phaser-example
</template>

<script>


export default {
  name: 'gameComponent',
  props: [],
  data () {
    return {
      game: null,
    }
  },
  mounted(){
    this.loadGame('wavey.js')
  },
  methods: {
    loadFile(fileName){
      let js = document.createElement("script");
          js.type = "text/javascript";
          js.src = `${fileName}`;
          document.body.appendChild(js);
          let res = js.onload = (() => {
            
          })
    },
    loadGame(fileName){
      // remove old game first
      if(this.game !== null){
        this.game.destroy()
      }
      // load new one
      let js = document.createElement("script");
          js.type = "text/javascript";
          js.src = `src/phaser/${fileName}`;
          document.body.appendChild(js);
          js.onload = (() => {
            __phaser.main.init(this.$el, this, {width: 800, height: 600});
          })
    }
  },
  destroyed() {
    this.game.destroy();
  }
}
</script>


<style lang="sass" scoped>

</style>
