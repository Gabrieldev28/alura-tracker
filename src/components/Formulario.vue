<template>
  <div class="flex p-8 bg-white shadow-lg">
    <div class="flex w-full">
      <div class="flex w-5/8" role="form" aria-label="Formulario para criação de uma nova tarefa">
        <input type="text" placeholder="Qual tarefa você deseja iniciar?" class="w-full p-2 outline-1 outline-mauve-400 rounded-sm" />
      </div>
      <div class="flex w-3/8 items-center justify-between gap-4 px-4">
        <section>
          <b>{{tempoFormatado}}</b>
        </section>
        <button @click="iniciar" class="flex border p-2 rounded gap-1">
          <span>
            <font-awesome-icon icon="play" />
          </span>
          <span>Play</span>
        </button>
        <button @click="finalizar" class="flex border p-2 rounded gap-1">
          <span>
            <font-awesome-icon icon="stop" />
          </span>
          <span>Stop</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'

const tempo = ref(0)
const tempoFormatado = computed(() => {
  const horas = String(Math.floor(tempo.value / 3600)).padStart(2, '0')
  const minutos = String(Math.floor((tempo.value % 3600) / 60)).padStart(2, '0')
  const segundos = String(tempo.value % 60).padStart(2, '0')

  return `${horas}:${minutos}:${segundos}`
})
let intervalo: ReturnType<typeof setInterval> | null = null

function iniciar() {
  if (intervalo) return // evita múltiplos timers

  intervalo = setInterval(() => {
    tempo.value++
  }, 1000)
}

function finalizar() {
  if (intervalo) {
    clearInterval(intervalo)
    intervalo = null
  }
}
</script>
