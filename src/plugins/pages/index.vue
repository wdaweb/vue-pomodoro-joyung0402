<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <h1>目前事項</h1>
        <h2>剩餘時間</h2>
      </v-col>
      <v-col cols="12">
        <v-btn icon="mdi-play" @click="startTimer"></v-btn>
        <v-btn icon="mdi-pause" @click="pauseTimer"></v-btn>
        <v-btn icon="mdi-skip-next" @click="skipTimer"></v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { definePage } from 'vue-router/auto'
import { useListStore } from '@/stores/list'
import { useSettingsStore } from '@/stores/settings'
import { storeToRefs } from 'pinia'
import { ref } from 'vue'

definePage({
  meta: {
    title: '番茄鐘'
  }
})

const STATUS = {
  STOP: 0,
  COUNTING: 1,
  PAUSE: 2
}
const status = ref(STATUS.STOP)
status.value = STATUS.PAUSE

const list = useListStore()
const { currentItem, items, timeleft } = storeToRefs(list)
const { setCurrentItem } = list

const settings = useSettingsStore()

let timer = 0
const startTimer = () => {
  if (status.value === STATUS.STOP && items.value.length > 0) {
    setCurrentItem()
  }

  timer = setInterval(() => {

  }, 1000)
}
</script>
