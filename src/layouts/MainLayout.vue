<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>

      <q-toolbar-title>
        CS Assessment Game
      </q-toolbar-title>

      <div>Quasar v{{ $q.version }}</div>

    </q-header>


    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'


export default defineComponent({
  name: 'MainLayout',

  components: {
  },

  setup() {


    return {

    }
  }
})
</script>
