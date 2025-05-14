<template>
  <div class="scroll-container">
    <div class="scroll-content" :style="{ animationDuration: animationDuration + 's' }">
      <div
          v-for="(symbol, index) in duplicatedSymbols"
          :key="index"
          class="tradingview-widget-wrapper"
      >
        <div class="tradingview-widget-container">
          <div
              class="tradingview-widget-container__widget"
              :ref="el => initWidget(el, symbol)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, nextTick, computed } from 'vue'

const originalSymbols = [
  'NASDAQ:AAPL',
  'NASDAQ:TSLA',
  'NASDAQ:GOOGL',
  'NASDAQ:MSFT',
  'NASDAQ:AMZN',
  'NASDAQ:NFLX',
  'NASDAQ:NVDA'
]

// Дублируем массив вручную для seamless loop
const duplicatedSymbols = [...originalSymbols, ...originalSymbols]

function initWidget(container, symbol) {
  if (!container) return

  const script = document.createElement('script')
  script.src = 'https://s3.tradingview.com/external-embedding/embed-widget-symbol-info.js'
  script.async = true
  script.innerHTML = JSON.stringify({
    symbol,
    width: '100%',
    locale: 'en',
    colorTheme: 'dark',
    isTransparent: false
  })

  container.innerHTML = ''
  container.appendChild(script)
}

// Расчёт длительности скролла исходя из количества элементов
const animationDuration = computed(() => duplicatedSymbols.length * 5) // 5s на элемент
</script>

<style scoped>
.scroll-container {
  height: 100vh;
  overflow: hidden;
  position: relative;
}

.scroll-content {
  display: flex;
  flex-direction: column;
  animation-name: scroll-up;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}

@keyframes scroll-up {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-50%);
  }
}

.tradingview-widget-wrapper {
  height: 20vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.tradingview-widget-container {
  width: 100%;
  height: 100%;
}
</style>
