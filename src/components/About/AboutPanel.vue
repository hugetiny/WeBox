<template>
    <div class="app-info">
<!--      <div class="app-version">-->
<!--        <span>Electron {{version}}</span>-->
<!--      </div>-->
      <div class="app-icon"></div>
      <div class="engine-info" v-if="!!engineInfo">
        <h4>{{ $t('engine-version') }}</h4>
        <h6>{{engineInfo}}</h6>
      </div>
    </div>
</template>

<script>

import { mapState } from 'vuex'

export default {
  name: 'about-panel',
  props: {
    visible: {
      type: Boolean,
      default: false
    }
  },
  data () {
    const version = this.$q.electron.remote.app.getVersion()
    return {
      version
    }
  },
  computed: {
    ...mapState('app', {
      engineInfo: state => state.engineInfo
    })
  },
  created () {
    this.$store.dispatch('app/fetchEngineInfo')
  }
}
</script>

<style lang="scss">
</style>
