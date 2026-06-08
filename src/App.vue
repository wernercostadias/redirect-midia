<script setup>
import { onMounted, ref } from 'vue'

const checkoutUrl = 'https://checkout.familiadepremios.com.br/?pdv_code=l0041m'
const isLoading = ref(false)
const isPageLoading = ref(true)

onMounted(() => {
  window.setTimeout(() => {
    isPageLoading.value = false
  }, 850)
})

function goToCheckout() {
  if (isLoading.value) {
    return
  }

  isLoading.value = true

  window.setTimeout(() => {
    window.location.href = checkoutUrl
  }, 900)
}
</script>

<template>
  <div v-if="isPageLoading" class="page-loader" aria-live="polite" aria-busy="true">
    <div class="page-loader__card">
      <span class="page-loader__spinner" aria-hidden="true"></span>
      <p class="page-loader__text">Carregando...</p>
    </div>
  </div>

  <main v-else class="page-shell">
    <section class="hero-card">

      <div class="hero-copy">
        <p class="eyebrow">Ambiente protegido</p>
        <h1>Você está quase lá!</h1>
        <p class="subtitle">
          Para continuar com sua participação, clique no botão abaixo.
        </p>
      </div>

      <div class="content-card">

        <button
          type="button"
          class="checkout-button"
          :class="{ 'is-loading': isLoading }"
          :disabled="isLoading"
          @click="goToCheckout"
        >
          <span v-if="isLoading" class="spinner" aria-hidden="true"></span>
          <span>{{ isLoading ? 'Carregando...' : 'Clique para continuar' }}</span>
        </button>

        <p class="helper-text">
          Você será direcionado para o checkout oficial.
        </p>
      </div>
    </section>
  </main>
</template>

<style>
:root {
  color-scheme: light;
  --green-main: #4f8500;
  --green-dark: #3f7100;
  --green-light: #c7e99b;
  --surface: #f5f7f4;
  --text-main: #17233a;
  --border: #4b5563;
  --white: #ffffff;
}

* {
  box-sizing: border-box;
}

html,
body,
#app {
  min-height: 100%;
  margin: 0;
}

body {
  font-family: 'Manrope', sans-serif;
  background:
    radial-gradient(circle at top, rgba(199, 233, 155, 1), transparent 58%),
    radial-gradient(circle at bottom, rgba(79, 133, 0, 0.2), transparent 48%),
    linear-gradient(180deg, #f2f9e8 0%, #edf6df 52%, #e8f2d7 100%);
  color: var(--text-main);
  background-attachment: fixed;
}

button,
input,
textarea,
select {
  font: inherit;
}

.page-shell {
  min-height: 100vh;
  display: grid;
  place-items: center;
  padding: 24px;
}

.page-loader {
  min-height: 100vh;
  display: grid;
  place-items: center;
  padding: 24px;
}

.page-loader__card {
  min-width: min(100%, 320px);
  padding: 28px 32px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.94);
  border: 1px solid rgba(79, 133, 0, 0.18);
  box-shadow: 0 24px 60px rgba(23, 35, 58, 0.12);
  display: grid;
  justify-items: center;
  gap: 14px;
}

.page-loader__spinner {
  width: 42px;
  height: 42px;
  border: 4px solid rgba(79, 133, 0, 0.2);
  border-top-color: var(--green-main);
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}

.page-loader__text {
  margin: 0;
  color: var(--green-dark);
  font-size: 1rem;
  font-weight: 800;
  letter-spacing: 0.02em;
}

.hero-card {
  width: min(100%, 560px);
  position: relative;
  padding: 72px 24px 28px;
  border: 1px solid rgba(75, 85, 99, 0.2);
  border-radius: 28px;
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 24px 60px rgba(23, 35, 58, 0.12);
  overflow: hidden;
}

.hero-card::before {
  content: '';
  position: absolute;
  inset: 0 0 auto;
  height: 10px;
  background: linear-gradient(90deg, var(--green-main), var(--green-light));
}

.badge {
  position: absolute;
  top: 18px;
  left: 24px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 16px;
  border-radius: 999px;
  background: var(--green-main);
  color: var(--white);
  font-size: 0.9rem;
  font-weight: 800;
  letter-spacing: 0.02em;
  box-shadow: 0 12px 28px rgba(79, 133, 0, 0.28);
}

.hero-copy {
  text-align: center;
}

.eyebrow {
  margin: 0 0 12px;
  color: var(--green-dark);
  font-size: 0.95rem;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

h1 {
  margin: 0;
  font-size: clamp(2rem, 5vw, 3.3rem);
  line-height: 1;
  letter-spacing: -0.04em;
}

.subtitle {
  max-width: 36ch;
  margin: 18px auto 0;
  font-size: 1.05rem;
  line-height: 1.6;
  color: rgba(23, 35, 58, 0.78);
}

.content-card {
  margin-top: 32px;
  padding: 22px;
  border: 1px solid rgba(79, 133, 0, 0.18);
  border-radius: 22px;
  background: linear-gradient(180deg, #ffffff 0%, #f8fbf3 100%);
}

.security-mark {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 14px 16px;
  border: 1px solid rgba(79, 133, 0, 0.16);
  border-radius: 18px;
  background: rgba(199, 233, 155, 0.22);
  color: var(--text-main);
  font-size: 0.98rem;
  line-height: 1.5;
}

.shield {
  width: 32px;
  height: 32px;
  flex: 0 0 32px;
  display: inline-grid;
  place-items: center;
  border-radius: 50%;
  background: var(--green-main);
  color: var(--white);
  font-weight: 800;
}

.checkout-button {
  width: 100%;
  margin-top: 20px;
  padding: 18px 22px;
  border: 0;
  border-radius: 18px;
  background: linear-gradient(180deg, var(--green-main) 0%, var(--green-dark) 100%);
  color: var(--white);
  font-size: 1rem;
  font-weight: 800;
  cursor: pointer;
  transition:
    transform 160ms ease,
    box-shadow 160ms ease,
    filter 160ms ease;
  box-shadow: 0 18px 30px rgba(79, 133, 0, 0.26);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
}

.checkout-button:hover {
  transform: translateY(-1px);
  filter: brightness(1.03);
  box-shadow: 0 20px 34px rgba(79, 133, 0, 0.32);
}

.checkout-button:disabled {
  cursor: wait;
}

.checkout-button.is-loading {
  transform: none;
  filter: none;
}

.checkout-button:focus-visible {
  outline: 3px solid rgba(79, 133, 0, 0.25);
  outline-offset: 3px;
}

.spinner {
  width: 18px;
  height: 18px;
  border: 2px solid rgba(255, 255, 255, 0.35);
  border-top-color: var(--white);
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}

.helper-text {
  margin: 14px 0 0;
  text-align: center;
  color: rgba(23, 35, 58, 0.7);
  font-size: 0.95rem;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

@media (max-width: 640px) {
  .page-shell {
    padding: 16px;
  }

  .hero-card {
    padding: 72px 18px 20px;
    border-radius: 24px;
  }

  .badge {
    left: 18px;
    right: 18px;
    justify-content: center;
    text-align: center;
  }

  .content-card {
    padding: 18px;
  }

  .security-mark {
    align-items: flex-start;
  }
}
</style>
