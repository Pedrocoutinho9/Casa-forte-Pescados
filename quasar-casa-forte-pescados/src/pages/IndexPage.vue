<template>
  <q-page>
    <!-- Carrossel Banner -->
    <section class="carousel-section">
      <q-carousel
        v-model="carouselSlide"
        animated
        arrows
        infinite
        autoplay
        :autoplay-interval="5000"
        transition-prev="slide-right"
        transition-next="slide-left"
        class="hero-carousel"
      >
        <q-carousel-slide :name="1" class="carousel-slide">
          <q-img
            src="/imagens/salmao.jpeg"
            alt="Salmão Fresco"
            class="carousel-img"
            fit="cover"
          />
          <div class="carousel-caption">Pescados Frescos Diariamente</div>
        </q-carousel-slide>

        <q-carousel-slide :name="2" class="carousel-slide">
          <q-img
            src="/imagens/Camarao.jpeg"
            alt="Camarão Grande"
            class="carousel-img"
            fit="cover"
          />
          <div class="carousel-caption">Direto do Mar para sua Mesa</div>
        </q-carousel-slide>

        <q-carousel-slide :name="3" class="carousel-slide">
          <q-img
            src="/imagens/Aneis.jpeg"
            alt="Anéis de Lula"
            class="carousel-img"
            fit="cover"
          />
          <div class="carousel-caption">A Melhor Seleção de Recife</div>
        </q-carousel-slide>
      </q-carousel>
    </section>

    <!-- Seção Home / Benefícios -->
    <section id="home" class="benefits-section">
      <div class="intro-header text-center q-mb-xl">
        <h2 class="text-h3 text-weight-bold text-primary q-mb-md">
          Do mar direto para sua porta
        </h2>
        <p class="text-subtitle1 text-grey-7">
          Na Pescados Casa Forte, selecionamos o melhor para você.
        </p>
      </div>

      <div class="row justify-center q-gutter-lg">
        <div class="col-12 col-sm-4 col-md-3">
          <q-card flat class="benefit-card text-center q-pa-lg">
            <div class="icon-box q-mb-md">🌊</div>
            <h3 class="text-h6 text-weight-bold text-primary q-mb-sm">100% Frescos</h3>
            <p class="text-body2 text-grey-7">
              Pescados selecionados diariamente para garantir o sabor.
            </p>
          </q-card>
        </div>

        <div class="col-12 col-sm-4 col-md-3">
          <q-card flat class="benefit-card text-center q-pa-lg">
            <div class="icon-box q-mb-md">🛵</div>
            <h3 class="text-h6 text-weight-bold text-primary q-mb-sm">Delivery Rápido</h3>
            <p class="text-body2 text-grey-7">
              Entregamos na sua casa com toda a segurança e higiene.
            </p>
          </q-card>
        </div>

        <div class="col-12 col-sm-4 col-md-3">
          <q-card flat class="benefit-card text-center q-pa-lg">
            <div class="icon-box q-mb-md">❄️</div>
            <h3 class="text-h6 text-weight-bold text-primary q-mb-sm">Embalagem Ideal</h3>
            <p class="text-body2 text-grey-7">
              Seu pedido chega na temperatura perfeita para o consumo.
            </p>
          </q-card>
        </div>
      </div>
    </section>

    <!-- Seção Produtos -->
    <section id="products" class="products-section">
      <h2 class="section-title text-h4 text-weight-bold text-primary text-center q-mb-xl">
        Nossos Produtos
      </h2>

      <div class="products-carousel-wrapper">
        <q-btn
          round
          color="primary"
          icon="chevron_left"
          class="carousel-arrow arrow-left"
          @click="scrollProducts('left')"
        />

        <div ref="productsCarousel" class="products-carousel">
          <q-card
            v-for="product in products"
            :key="product.name"
            class="product-card"
          >
            <q-img
              :src="product.image"
              :alt="product.name"
              class="product-img"
              fit="cover"
            />
            <q-card-section class="text-center">
              <h3 class="text-h6 text-weight-bold text-primary q-mb-xs">
                {{ product.name }}
              </h3>
              <p class="text-body2 text-grey-7 q-mb-md">
                {{ product.description }}
              </p>
              <q-btn
                unelevated
                color="positive"
                label="Pedir Agora"
                class="btn-delivery"
                href="https://wa.me/558130718296"
                target="_blank"
                no-caps
              />
            </q-card-section>
          </q-card>
        </div>

        <q-btn
          round
          color="primary"
          icon="chevron_right"
          class="carousel-arrow arrow-right"
          @click="scrollProducts('right')"
        />
      </div>
    </section>

    <!-- Seção Sobre Nós -->
    <section id="about" class="about-section">
      <div class="row items-stretch">
        <div class="col-12 col-md-6 about-text q-pa-xl">
          <h2 class="text-h4 text-weight-bold text-primary q-mb-lg">
            Sobre a Casa Forte Pescados
          </h2>
          <p class="text-body1 text-grey-8 q-mb-md" style="line-height: 1.8">
            A <strong>Pescados Casa Forte</strong> nasceu da junção de uma paixão
            profunda pelos frutos do mar e o desejo de levar qualidade superior
            para os momentos em que você está perto de quem gosta.
          </p>
          <p class="text-body1 text-grey-8 q-mb-md" style="line-height: 1.8">
            Não somos apenas uma peixaria, somos seus parceiros na cozinha.
            Trabalhamos com curadoria rigorosa para garantir que cada peixe,
            camarão ou lagosta entregue mantenha o frescor e o sabor autêntico
            do mar.
          </p>
          <p class="text-body1 text-grey-8" style="line-height: 1.8">
            Localizados no coração da Zona Norte, estamos prontos para atender você.
          </p>
        </div>
        <div class="col-12 col-md-6 about-image">
          <q-img
            src="/imagens/salmao.jpeg"
            alt="Nossa bancada de peixes"
            fit="cover"
            class="full-height"
          />
        </div>
      </div>
    </section>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const carouselSlide = ref(1)
const productsCarousel = ref(null)

const products = ref([
  {
    name: 'Peixes Frescos',
    description: 'Variedade do dia',
    image: '/imagens/agulha.jpeg'
  },
  {
    name: 'Camarão',
    description: 'Limpo e descascado',
    image: '/imagens/Camarao.jpeg'
  },
  {
    name: 'Polvo',
    description: 'Tenro e saboroso',
    image: '/imagens/Polvo.jpeg'
  },
  {
    name: 'Anéis de Lula',
    description: 'Prontos para preparo',
    image: '/imagens/Aneis.jpeg'
  },
  {
    name: 'Marisco',
    description: 'Fresco e selecionado',
    image: '/imagens/Marisco.jpeg'
  },
  {
    name: 'Posta de Peixe',
    description: 'Corte especial',
    image: '/imagens/posta.jpeg'
  }
])

function scrollProducts(direction) {
  if (productsCarousel.value) {
    const scrollAmount = 340
    productsCarousel.value.scrollBy({
      left: direction === 'right' ? scrollAmount : -scrollAmount,
      behavior: 'smooth'
    })
  }
}
</script>

<style lang="scss" scoped>
// Carrossel Hero
.carousel-section {
  width: 100%;
  height: 70vh;
  min-height: 400px;
}

.hero-carousel {
  height: 100%;
}

.carousel-slide {
  padding: 0;
}

.carousel-img {
  height: 100%;
  width: 100%;
  filter: brightness(0.85);
}

.carousel-caption {
  position: absolute;
  bottom: 15%;
  left: 5%;
  background: rgba(36, 50, 82, 0.9);
  color: white;
  padding: 20px 40px;
  border-radius: 0 50px 50px 0;
  font-size: 1.8rem;
  font-weight: bold;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

// Seção Benefícios
.benefits-section {
  background: white;
  padding: 60px 5%;
  border-bottom: 1px solid #eee;
}

.benefit-card {
  background: transparent;
}

.icon-box {
  font-size: 3rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 15px;
  background: #f8fbfc;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
}

// Seção Produtos
.products-section {
  padding: 60px 0;
  background: white;
}

.section-title {
  position: relative;
  
  &::after {
    content: '';
    display: block;
    width: 60px;
    height: 4px;
    background: #0d6b82;
    margin: 10px auto 0;
    border-radius: 2px;
  }
}

.products-carousel-wrapper {
  position: relative;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.products-carousel {
  display: flex;
  gap: 30px;
  overflow-x: auto;
  scroll-behavior: smooth;
  padding: 20px 5%;
  width: 100%;
  scrollbar-width: none;
  -ms-overflow-style: none;
  
  &::-webkit-scrollbar {
    display: none;
  }
}

.product-card {
  min-width: 260px;
  flex: 0 0 auto;
  border-radius: 15px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
  border: 1px solid #eee;
  transition: transform 0.3s ease;
  
  &:hover {
    transform: translateY(-5px);
  }
}

.product-img {
  height: 300px;
  border-radius: 15px 15px 0 0;
}

.btn-delivery {
  font-size: 1rem;
  padding: 12px 25px;
  border-radius: 50px;
  box-shadow: 0 4px 10px rgba(37, 211, 102, 0.3);
}

.carousel-arrow {
  position: absolute;
  z-index: 10;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  
  &.arrow-left {
    left: 20px;
  }
  
  &.arrow-right {
    right: 20px;
  }
}

// Seção Sobre
.about-section {
  background: white;
  min-height: 500px;
}

.about-text {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.about-image {
  min-height: 400px;
}

// Responsivo
@media (max-width: 768px) {
  .carousel-section {
    height: 50vh;
  }
  
  .carousel-caption {
    font-size: 1.2rem;
    padding: 10px 20px;
    width: 90%;
  }
  
  .carousel-arrow {
    width: 40px;
    height: 40px;
    
    &.arrow-left {
      left: 10px;
    }
    
    &.arrow-right {
      right: 10px;
    }
  }
  
  .about-section .row {
    flex-direction: column-reverse;
  }
  
  .about-image {
    min-height: 300px;
  }
}
</style>
