<template>
  <div class="pricing-page">
    <div class="page-header">
      <h1>{{ $t('pricing.title') }}</h1>
      <p>{{ $t('pricing.subtitle') }}</p>
    </div>
    <div class="container">
      <div class="pricing-content">
        <section class="pricing-section">
          <h2>{{ $t('pricing.pricePlan') }}</h2>
          <div class="pricing-cards">
            <div class="pricing-card">
              <h3>{{ $t('pricing.basic.name') }}</h3>
              <div class="price">
                <span class="currency">¥</span>
                <span class="amount">{{ $t('pricing.basic.price') }}</span>
                <span class="period">{{ $t('pricing.basic.period') }}</span>
              </div>
              <ul class="features-list">
                <li>✓ {{ $t('pricing.basic.features.feature1') }}</li>
                <li>✓ {{ $t('pricing.basic.features.feature2') }}</li>
                <li>✓ {{ $t('pricing.basic.features.feature3') }}</li>
                <li>✓ {{ $t('pricing.basic.features.feature4') }}</li>
              </ul>
              <n-button type="primary" block @click="handleContact">{{ $t('pricing.basic.button') }}</n-button>
            </div>
            <div class="pricing-card featured">
              <div class="badge">{{ $t('pricing.recommended') }}</div>
              <h3>{{ $t('pricing.professional.name') }}</h3>
              <div class="price">
                <span class="currency">¥</span>
                <span class="amount">{{ $t('pricing.professional.price') }}</span>
                <span class="period">{{ $t('pricing.professional.period') }}</span>
              </div>
              <ul class="features-list">
                <li>✓ {{ $t('pricing.professional.features.feature1') }}</li>
                <li>✓ {{ $t('pricing.professional.features.feature2') }}</li>
                <li>✓ {{ $t('pricing.professional.features.feature3') }}</li>
                <li>✓ {{ $t('pricing.professional.features.feature4') }}</li>
                <li>✓ {{ $t('pricing.professional.features.feature5') }}</li>
                <li>✓ {{ $t('pricing.professional.features.feature6') }}</li>
              </ul>
              <n-button type="primary" block @click="handleContact">{{ $t('pricing.professional.button') }}</n-button>
            </div>
            <div class="pricing-card">
              <h3>{{ $t('pricing.enterprise.name') }}</h3>
              <div class="price">
                <span class="currency">¥</span>
                <span class="amount">{{ $t('pricing.enterprise.price') }}</span>
              </div>
              <ul class="features-list">
                <li>✓ {{ $t('pricing.enterprise.features.feature1') }}</li>
                <li>✓ {{ $t('pricing.enterprise.features.feature2') }}</li>
                <li>✓ {{ $t('pricing.enterprise.features.feature3') }}</li>
                <li>✓ {{ $t('pricing.enterprise.features.feature4') }}</li>
                <li>✓ {{ $t('pricing.enterprise.features.feature5') }}</li>
                <li>✓ {{ $t('pricing.enterprise.features.feature6') }}</li>
              </ul>
              <n-button type="primary" block @click="handleContact">{{ $t('pricing.enterprise.button') }}</n-button>
            </div>
          </div>
        </section>

        <section class="why-choose-section">
          <h2>{{ $t('pricing.whyChoose') }}</h2>
          <div class="reasons-grid">
            <div
              v-for="reason in reasons"
              :key="reason.id"
              class="reason-item"
            >
              <div class="reason-icon">{{ reason.icon }}</div>
              <h3>{{ reason.title }}</h3>
              <p>{{ reason.description }}</p>
            </div>
          </div>
        </section>

        <section class="comparison-section">
          <h2>{{ $t('pricing.comparison') }}</h2>
          <div class="comparison-table">
            <table>
              <thead>
                <tr>
                  <th>{{ $t('pricing.comparisonTable.featureComparison') }}</th>
                  <th>{{ $t('pricing.comparisonTable.weican') }}</th>
                  <th>{{ $t('pricing.comparisonTable.traditionalPOS') }}</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>{{ $t('pricing.comparisonTable.cloudSync') }}</td>
                  <td>✓</td>
                  <td>✗</td>
                </tr>
                <tr>
                  <td>{{ $t('pricing.comparisonTable.mobileManagement') }}</td>
                  <td>✓</td>
                  <td>✗</td>
                </tr>
                <tr>
                  <td>{{ $t('pricing.comparisonTable.memberMarketing') }}</td>
                  <td>✓</td>
                  <td>{{ $t('pricing.comparisonTable.extraFee') }}</td>
                </tr>
                <tr>
                  <td>{{ $t('pricing.comparisonTable.onlineOrdering') }}</td>
                  <td>✓</td>
                  <td>✗</td>
                </tr>
                <tr>
                  <td>{{ $t('pricing.comparisonTable.multiStore') }}</td>
                  <td>✓</td>
                  <td>{{ $t('pricing.comparisonTable.extraFee') }}</td>
                </tr>
                <tr>
                  <td>{{ $t('pricing.comparisonTable.price') }}</td>
                  <td>{{ $t('pricing.comparisonTable.moreAffordable') }}</td>
                  <td>{{ $t('pricing.comparisonTable.higher') }}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useRouter } from 'vue-router'
import { useI18n } from 'vue-i18n'
import { NButton } from 'naive-ui'

const router = useRouter()
const { t } = useI18n()

const reasons = computed(() => [
  {
    id: 1,
    icon: '💰',
    title: t('pricing.reasons.reason1.title'),
    description: t('pricing.reasons.reason1.description')
  },
  {
    id: 2,
    icon: '🚀',
    title: t('pricing.reasons.reason2.title'),
    description: t('pricing.reasons.reason2.description')
  },
  {
    id: 3,
    icon: '📊',
    title: t('pricing.reasons.reason3.title'),
    description: t('pricing.reasons.reason3.description')
  },
  {
    id: 4,
    icon: '🔧',
    title: t('pricing.reasons.reason4.title'),
    description: t('pricing.reasons.reason4.description')
  },
  {
    id: 5,
    icon: '💬',
    title: t('pricing.reasons.reason5.title'),
    description: t('pricing.reasons.reason5.description')
  },
  {
    id: 6,
    icon: '🔒',
    title: t('pricing.reasons.reason6.title'),
    description: t('pricing.reasons.reason6.description')
  }
])

const handleContact = () => {
  router.push('/contact')
}
</script>

<style scoped>
.pricing-page {
  padding: 60px 0;
  min-height: 60vh;
}

.page-header {
  text-align: center;
  padding: 60px 24px;
  background: linear-gradient(135deg, #18a058 0%, #36ad6a 100%);
  color: #fff;
}

.page-header h1 {
  font-size: 48px;
  font-weight: 700;
  margin-bottom: 16px;
}

.page-header p {
  font-size: 20px;
  opacity: 0.9;
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 60px 24px;
}

.pricing-section {
  margin-bottom: 80px;
}

.pricing-section h2 {
  font-size: 36px;
  font-weight: 700;
  text-align: center;
  margin-bottom: 50px;
  color: #1a1a1a;
}

.pricing-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  max-width: 1200px;
  margin: 0 auto;
}

.pricing-card {
  background: #fff;
  border: 2px solid #eee;
  border-radius: 12px;
  padding: 40px 30px;
  text-align: center;
  position: relative;
  transition: all 0.3s;
}

.pricing-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
}

.pricing-card.featured {
  border-color: #18a058;
  box-shadow: 0 4px 16px rgba(24, 160, 88, 0.2);
}

.badge {
  position: absolute;
  top: -12px;
  left: 50%;
  transform: translateX(-50%);
  background: #18a058;
  color: #fff;
  padding: 4px 16px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
}

.pricing-card h3 {
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 24px;
  color: #1a1a1a;
}

.price {
  margin-bottom: 30px;
}

.currency {
  font-size: 20px;
  color: #666;
  vertical-align: top;
}

.amount {
  font-size: 48px;
  font-weight: 700;
  color: #18a058;
}

.period {
  font-size: 16px;
  color: #666;
  margin-left: 4px;
}

.features-list {
  list-style: none;
  text-align: left;
  margin-bottom: 30px;
  padding: 0;
}

.features-list li {
  padding: 12px 0;
  color: #333;
  font-size: 15px;
}

.why-choose-section,
.comparison-section {
  margin-bottom: 80px;
}

.why-choose-section h2,
.comparison-section h2 {
  font-size: 36px;
  font-weight: 700;
  text-align: center;
  margin-bottom: 50px;
  color: #1a1a1a;
}

.reasons-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
}

.reason-item {
  background: #f8f9fa;
  padding: 30px;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s;
}

.reason-item:hover {
  background: #fff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transform: translateY(-3px);
}

.reason-icon {
  font-size: 48px;
  margin-bottom: 16px;
}

.reason-item h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 12px;
  color: #1a1a1a;
}

.reason-item p {
  color: #666;
  font-size: 14px;
  line-height: 1.6;
}

.comparison-table {
  overflow-x: auto;
}

.comparison-table table {
  width: 100%;
  border-collapse: collapse;
  background: #fff;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.comparison-table th,
.comparison-table td {
  padding: 16px 24px;
  text-align: left;
  border-bottom: 1px solid #eee;
}

.comparison-table th {
  background: #18a058;
  color: #fff;
  font-weight: 600;
}

.comparison-table tr:last-child td {
  border-bottom: none;
}

.comparison-table tr:hover {
  background: #f8f9fa;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 32px;
  }

  .pricing-cards {
    grid-template-columns: 1fr;
  }

  .reasons-grid {
    grid-template-columns: 1fr;
  }
}
</style>
