<template>
  <div class='col-6 align-self-center text-right pr-0'>
    <button class='btn btn-link' @click='clickShowLog' title='Show Log'>
      <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <line x1="8" y1="6" x2="21" y2="6"></line>
        <line x1="8" y1="12" x2="21" y2="12"></line>
        <line x1="8" y1="18" x2="21" y2="18"></line>
        <line x1="3" y1="6" x2="3" y2="6"></line>
        <line x1="3" y1="12" x2="3" y2="12"></line>
        <line x1="3" y1="18" x2="3" y2="18"></line>
      </svg>
    </button>
    <button class='btn btn-link' @click='clickAutostart' v-html='autostartIcon' :title='autostartButtonTitle'></button>
    <button class='btn btn-link' @click='clickSound' v-html='soundIcon' :title='soundButtonTitle'></button>
  </div>
</template>

<script>
export default {
  // PascalCase, e.g. ThisIsAnExample
  name: 'ControlPanel',

  // variables
  data () {
    return {
    }
  },
  computed: {
    autostartNextInterval () {
      return (this.$store && this.$store.state.autostartNextInterval)
    },
    autostartButtonTitle () {
      return 'Autostart Next Interval is ' +
             (this.autostartNextInterval ? 'ON' : 'OFF')
    },
    autostartIcon () {
      const SVG_AUTOSTART_ON = '<svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" ' +
                            'stroke-linecap="round" stroke-linejoin="round"> ' +
                            '<polyline points="23 4 23 10 17 10"></polyline> ' +
                            '<polyline points="1 20 1 14 7 14"></polyline> ' +
                            '<path d="M3.51 9a9 9 0 0 1 14.85-3.36L23 10M1 14l4.64 4.36A9 9 0 0 0 20.49 15"></path> ' +
                            '</svg>'
      const SVG_AUTOSTART_OFF = '<svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" ' +
                                'stroke-linecap="round" stroke-linejoin="round"> ' +
                                '<line x1="1" y1="1" x2="23" y2="23" class=""></line> ' +
                                '<polyline points="23 4 23 10 17 10"></polyline> ' +
                                '<polyline points="1 20 1 14 7 14"></polyline> ' +
                                '<path d="M3.51 9a9 9 0 0 1 14.85-3.36L23 10M1 14l4.64 4.36A9 9 0 0 0 20.49 15"></path> ' +
                                '</svg>'
      return (this.autostartNextInterval ? SVG_AUTOSTART_ON : SVG_AUTOSTART_OFF)
    },
    soundIsOn () {
      return (this.$store && this.$store.state.soundIsOn)
    },
    soundButtonTitle () {
      return 'Sound is ' +
             (this.soundIsOn ? 'ON' : 'OFF')
    },
    soundIcon () {
      const SVG_SOUND_OFF = '<svg width="32" height="32" viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="2" ' +
                            'stroke-linecap="round" stroke-linejoin="round"> ' +
                            '<path d="M20 16 C20 8 15 2 15 2 L8 10 2 10 2 22 8 22 15 30 C15 30 20 24 20 16 Z" /> ' +
                            '</svg>'
      const SVG_SOUND_ON = '<svg width="32" height="32" viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="2" ' +
                           'stroke-linecap="round" stroke-linejoin="round"> ' +
                           '<path d="M20 16 C20 8 15 2 15 2 L8 10 2 10 2 22 8 22 15 30 C15 30 20 24 20 16 Z M21 2 C21 2 25 6 25 16 25 26 21 30 21 30 M27 4 C27 4 30 8 30 16 30 24 27 28 27 28" /> ' +
                           '</svg>'
      return (this.soundIsOn ? SVG_SOUND_ON : SVG_SOUND_OFF)
    }
  },
  methods: {
    clickAutostart () {
      this.$store.commit('toggleAutostart')
    },
    clickShowLog () {
      this.$store.commit('openLog')
    },
    clickSound () {
      this.$store.commit('toggleSound')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn {
  color: orange;
  padding-left: 0px;  /* Too much spacing between buttons */
}

.btn:hover {
  color: #FED8B1;
}
</style>