<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          v-if="$route.fullPath.includes('/chat')"
          icon="arrow_back"
          flat
          dense
          label="Back"
          @click="$router.go(-1)"
        />

        <q-toolbar-title class="absolute-center">
          {{ title }}
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const title = computed(() => {
  let currentPath = route.fullPath
  let titleText = ''
  if (currentPath == '/') {
    titleText = 'SmackChat'
  } else if (currentPath == '/chat') {
    titleText = 'Chat'
  } else if (currentPath == '/auth') {
    titleText = 'Login'
  }
  return titleText
})
</script>
