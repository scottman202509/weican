<template>
  <div class="home">
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <h1 class="hero-title">{{ $t('home.title') }}</h1>
        <h2 class="hero-subtitle">{{ $t('home.subtitle') }}</h2>
        <p class="hero-description">
          {{ $t('home.description') }}
        </p>
        <n-button type="primary" size="large" class="hero-button" @click="handleConsult">
          {{ $t('common.immediately') }}
        </n-button>
      </div>
    </section>

    <!-- Restaurant Types Section -->
    <section class="restaurant-types">
      <div class="container">
        <h2 class="section-title">{{ $t('home.restaurantTypes') }}</h2>
        <div class="types-grid">
          <div
            v-for="type in restaurantTypes"
            :key="type.key"
            class="type-card"
            @click="handleTypeClick(type)"
          >
            <div class="type-icon">{{ type.icon }}</div>
            <h3>{{ type.name }}</h3>
            <p>{{ type.description }}</p>
            <span class="learn-more">{{ $t('common.learnMore') }} →</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="features">
      <div class="container">
        <div class="features-header">
          <h2 class="section-title">{{ $t('home.betterPrice') }}</h2>
          <p class="section-subtitle">{{ $t('home.betterPriceDesc') }}</p>
          <n-button type="primary" size="large" @click="handleConsult">{{ $t('common.immediately') }}</n-button>
        </div>
      </div>
    </section>

    <!-- Customer Cases Section -->
    <section class="customer-cases">
      <div class="container">
        <h2 class="section-title">{{ $t('home.customerCases') }}</h2>
        <div class="cases-grid">
          <div
            v-for="caseItem in customerCases"
            :key="caseItem.id"
            class="case-card"
          >
            <div class="case-quote">"{{ caseItem.quote }}"</div>
            <div class="case-info">
              <h3>{{ caseItem.name }}</h3>
              <p>{{ caseItem.location }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Product Showcase Section -->
    <section class="product-showcase">
      <div class="container">
        <h2 class="section-title">{{ $t('home.productShowcase') }}</h2>
        <p class="section-subtitle">{{ $t('home.productShowcaseDesc') }}</p>
        <div class="products-grid">
          <div
            v-for="product in products"
            :key="product.id"
            class="product-card"
            @click="handleProductClick(product)"
          >
            <div class="product-icon">{{ product.icon }}</div>
            <h3>{{ product.name }}</h3>
            <p>{{ product.description }}</p>
            <span class="learn-more">{{ $t('common.learnMore') }} →</span>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
      <div class="container">
        <h2 class="cta-title">{{ $t('home.readyUpgrade') }}</h2>
        <p class="cta-description">
          {{ $t('home.readyUpgradeDesc') }}
        </p>
        <n-button type="primary" size="large" @click="handleConsult">
          {{ $t('home.getDemo') }}
        </n-button>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'
import { useI18n } from 'vue-i18n'
import { NButton } from 'naive-ui'

const router = useRouter()
const { t } = useI18n()

const restaurantTypes = computed(() => [
  { key: 'fast', name: t('home.restaurantTypesList.fast.name'), description: t('home.restaurantTypesList.fast.description'), icon: '🍔' },
  { key: 'dine-in', name: t('home.restaurantTypesList.dine-in.name'), description: t('home.restaurantTypesList.dine-in.description'), icon: '🍽️' },
  { key: 'tea', name: t('home.restaurantTypesList.tea.name'), description: t('home.restaurantTypesList.tea.description'), icon: '🧋' },
  { key: 'hotpot', name: t('home.restaurantTypesList.hotpot.name'), description: t('home.restaurantTypesList.hotpot.description'), icon: '🍲' },
  { key: 'buffet', name: t('home.restaurantTypesList.buffet.name'), description: t('home.restaurantTypesList.buffet.description'), icon: '🍱' },
  { key: 'korean', name: t('home.restaurantTypesList.korean.name'), description: t('home.restaurantTypesList.korean.description'), icon: '🍜' },
  { key: 'japanese', name: t('home.restaurantTypesList.japanese.name'), description: t('home.restaurantTypesList.japanese.description'), icon: '🍣' },
  { key: 'southeast', name: t('home.restaurantTypesList.southeast.name'), description: t('home.restaurantTypesList.southeast.description'), icon: '🍛' }
])

const customerCases = computed(() => [
  {
    id: 1,
    quote: t('home.customerCasesList.case1.quote'),
    name: t('home.customerCasesList.case1.name'),
    location: t('home.customerCasesList.case1.location')
  },
  {
    id: 2,
    quote: t('home.customerCasesList.case2.quote'),
    name: t('home.customerCasesList.case2.name'),
    location: t('home.customerCasesList.case2.location')
  },
  {
    id: 3,
    quote: t('home.customerCasesList.case3.quote'),
    name: t('home.customerCasesList.case3.name'),
    location: t('home.customerCasesList.case3.location')
  },
  {
    id: 4,
    quote: t('home.customerCasesList.case4.quote'),
    name: t('home.customerCasesList.case4.name'),
    location: t('home.customerCasesList.case4.location')
  },
  {
    id: 5,
    quote: t('home.customerCasesList.case5.quote'),
    name: t('home.customerCasesList.case5.name'),
    location: t('home.customerCasesList.case5.location')
  },
  {
    id: 6,
    quote: t('home.customerCasesList.case6.quote'),
    name: t('home.customerCasesList.case6.name'),
    location: t('home.customerCasesList.case6.location')
  }
])

const products = computed(() => [
  {
    id: 1,
    name: t('home.productsList.pos.name'),
    key: 'pos',
    description: t('home.productsList.pos.description'),
    icon: '💻'
  },
  {
    id: 2,
    name: t('home.productsList.handheld.name'),
    key: 'handheld',
    description: t('home.productsList.handheld.description'),
    icon: '📱'
  },
  {
    id: 3,
    name: t('home.productsList.tablet.name'),
    key: 'tablet',
    description: t('home.productsList.tablet.description'),
    icon: '📲'
  },
  {
    id: 4,
    name: t('home.productsList.kiosk.name'),
    key: 'kiosk',
    description: t('home.productsList.kiosk.description'),
    icon: '🖥️'
  },
  {
    id: 5,
    name: t('home.productsList.kds.name'),
    key: 'kds',
    description: t('home.productsList.kds.description'),
    icon: '📺'
  },
  {
    id: 6,
    name: t('home.productsList.delivery.name'),
    key: 'delivery',
    description: t('home.productsList.delivery.description'),
    icon: '🚀'
  }
])

const handleConsult = () => {
  router.push('/contact')
}

const handleTypeClick = (type) => {
  if (type.key) {
    router.push(`/solution/${type.key}`)
  }
}

const handleProductClick = (product) => {
  if (product.key) {
    router.push(`/product/${product.key}`)
  }
}
</script>

<style scoped>
.home {
  flex: 1;
}

/* Hero Section */
.hero {
  background: linear-gradient(135deg, #18a058 0%, #36ad6a 100%);
  color: #fff;
  padding: 120px 24px;
  text-align: center;
}

.hero-content {
  max-width: 800px;
  margin: 0 auto;
}

.hero-title {
  font-size: 56px;
  font-weight: 700;
  margin-bottom: 16px;
}

.hero-subtitle {
  font-size: 32px;
  font-weight: 600;
  margin-bottom: 24px;
  opacity: 0.95;
}

.hero-description {
  font-size: 18px;
  line-height: 1.8;
  margin-bottom: 40px;
  opacity: 0.9;
}

.hero-button {
  height: 50px;
  padding: 0 40px;
  font-size: 16px;
}

/* Container */
.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 24px;
}

/* Section Titles */
.section-title {
  font-size: 40px;
  font-weight: 700;
  text-align: center;
  margin-bottom: 16px;
  color: #1a1a1a;
}

.section-subtitle {
  font-size: 18px;
  text-align: center;
  color: #666;
  margin-bottom: 40px;
}

/* Restaurant Types Section */
.restaurant-types {
  padding: 80px 0;
  background: #f8f9fa;
}

.types-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
  margin-top: 50px;
}

.type-card {
  background: #fff;
  padding: 40px 30px;
  border-radius: 12px;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.type-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
}

.type-icon {
  font-size: 48px;
  margin-bottom: 20px;
}

.type-card h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 12px;
  color: #1a1a1a;
}

.type-card p {
  color: #666;
  margin-bottom: 20px;
  font-size: 14px;
}

.learn-more {
  color: #18a058;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s;
}

.learn-more:hover {
  color: #36ad6a;
}

/* Features Section */
.features {
  padding: 80px 0;
  background: #fff;
}

.features-header {
  text-align: center;
}

/* Customer Cases Section */
.customer-cases {
  padding: 80px 0;
  background: #f8f9fa;
}

.cases-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  margin-top: 50px;
}

.case-card {
  background: #fff;
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.case-quote {
  font-size: 18px;
  line-height: 1.8;
  color: #333;
  margin-bottom: 24px;
  font-style: italic;
}

.case-info h3 {
  font-size: 20px;
  font-weight: 600;
  color: #1a1a1a;
  margin-bottom: 8px;
}

.case-info p {
  color: #666;
  font-size: 14px;
}

/* Product Showcase Section */
.product-showcase {
  padding: 80px 0;
  background: #fff;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
  margin-top: 50px;
}

.product-card {
  background: #f8f9fa;
  padding: 40px 30px;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s;
  cursor: pointer;
}

.product-card:hover {
  background: #fff;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
  transform: translateY(-5px);
}

.product-icon {
  font-size: 64px;
  margin-bottom: 24px;
}

.product-card h3 {
  font-size: 22px;
  font-weight: 600;
  margin-bottom: 12px;
  color: #1a1a1a;
}

.product-card p {
  color: #666;
  margin-bottom: 20px;
  font-size: 14px;
}

/* CTA Section */
.cta-section {
  padding: 100px 0;
  background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);
  color: #fff;
  text-align: center;
}

.cta-title {
  font-size: 40px;
  font-weight: 700;
  margin-bottom: 20px;
}

.cta-description {
  font-size: 18px;
  margin-bottom: 40px;
  opacity: 0.9;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 36px;
  }

  .hero-subtitle {
    font-size: 24px;
  }

  .section-title {
    font-size: 28px;
  }

  .types-grid,
  .cases-grid,
  .products-grid {
    grid-template-columns: 1fr;
  }

  .cta-title {
    font-size: 28px;
  }
}
</style>

