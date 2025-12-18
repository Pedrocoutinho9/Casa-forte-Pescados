<template>
  <q-layout view="hHh lpR fFf">
    <!-- Header -->
    <q-header elevated class="bg-primary">
      <q-toolbar class="header-toolbar">
        <div class="logo-area">
          <router-link to="/" class="logo-link">
            <q-img
              src="/imagens/Logo.png"
              alt="Logotipo Pescados Casa Forte"
              class="logo-img"
              fit="contain"
            />
          </router-link>
          <span class="brand-name text-weight-bold">Casa Forte Pescados</span>
        </div>

        <q-space />

        <!-- Menu Desktop -->
        <nav class="gt-sm">
          <q-btn flat no-caps label="Home" to="/#home" class="nav-btn" />
          <q-btn flat no-caps label="Produtos" to="/#products" class="nav-btn" />
          <q-btn flat no-caps label="Sobre nós" to="/#about" class="nav-btn" />
          <q-btn flat no-caps label="Contato" to="/#contact" class="nav-btn" />
        </nav>

        <!-- Menu Mobile -->
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          class="lt-md"
          @click="toggleDrawer"
        />
      </q-toolbar>
    </q-header>

    <!-- Drawer Mobile -->
    <q-drawer
      v-model="drawerOpen"
      side="right"
      overlay
      behavior="mobile"
      class="bg-primary"
    >
      <q-list>
        <q-item clickable v-ripple to="/#home" @click="drawerOpen = false">
          <q-item-section class="text-white">Home</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/#products" @click="drawerOpen = false">
          <q-item-section class="text-white">Produtos</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/#about" @click="drawerOpen = false">
          <q-item-section class="text-white">Sobre nós</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/#contact" @click="drawerOpen = false">
          <q-item-section class="text-white">Contato</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <!-- Conteúdo Principal -->
    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-primary text-center footer-compact" id="contact">
      <div class="contact-content q-mb-sm">
        <h2 class="text-h6 text-weight-bold q-mb-sm">Fale Conosco</h2>
        <p class="q-my-xs"><strong>Email:</strong> info@pescadoscasaforte.com</p>
        <p class="q-my-xs"><strong>Telefone/Zap:</strong> (81) 3071-8296</p>
        <p class="q-my-xs"><strong>Instagram:</strong> @casafortepescados</p>
        <p class="q-my-xs">Estrada das Ubaias, 758, Loja 0010 - Casa Forte</p>
      </div>
      <q-separator dark class="q-my-sm" />
      <p class="text-caption text-grey-5 q-mt-sm q-mb-none">
        &copy; 2024 Casa Forte Pescados. Todos os direitos reservados.
      </p>
    </q-footer>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'

const drawerOpen = ref(false)

function toggleDrawer() {
  drawerOpen.value = !drawerOpen.value
}
</script>

<style lang="scss" scoped>
.header-toolbar {
  max-width: 1200px;
  margin: 0 auto;
  padding: 10px 20px;
}

.logo-area {
  display: flex;
  align-items: center;
  gap: 15px;
}

.logo-link {
  text-decoration: none;
}

.logo-img {
  height: 60px;
  width: 60px;
}

.brand-name {
  color: white;
  font-size: 1.2rem;
}

.nav-btn {
  font-size: 1.1rem;
  font-weight: 600;
  margin-left: 8px;

  &:hover {
    background: rgba(255, 255, 255, 0.15);
  }
}

.footer-compact {
  max-height: 282px;
  padding: 20px 24px !important;
  overflow: hidden;
}

.contact-content {
  p {
    margin: 6px 0;
    font-size: 1rem;
    opacity: 0.9;
  }
}
</style>
