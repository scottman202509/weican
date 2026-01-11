<template>
  <div class="about-page">
    <div class="page-header">
      <h1>{{ $t('about.title') }}</h1>
      <p>{{ $t('about.subtitle') }}</p>
    </div>
    <div class="container">
      <div class="about-content">
        <section class="about-section">
          <h2>{{ $t('about.companyIntro') }}</h2>
          <p>
            {{ $t('about.intro1') }}
          </p>
          <p>
            {{ $t('about.intro2') }}
          </p>
        </section>

        <section class="about-section">
          <h2>{{ $t('about.advantages') }}</h2>
          <div class="advantages-grid">
            <div
              v-for="advantage in advantages"
              :key="advantage.id"
              class="advantage-item"
            >
              <div class="advantage-icon">{{ advantage.icon }}</div>
              <h3>{{ advantage.title }}</h3>
              <p>{{ advantage.description }}</p>
            </div>
          </div>
        </section>

        <section class="about-section">
          <h2>{{ $t('about.contact') }}</h2>
          <div class="contact-info">
            <div class="contact-item">
              <strong>{{ $t('about.email') }}：</strong>contact@weican.com
            </div>
            <div class="contact-item">
              <strong>{{ $t('about.phone') }}：</strong>+81 0120046042
            </div>
            <div class="contact-item">
              <strong>{{ $t('about.address') }}：</strong>〒540-0012 Osaka, Chuo Ward, Tanimachi, 2 Chome−9−3 ザ・ファインタワー大手前 １Ｆ
            </div>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useI18n } from 'vue-i18n'

const { t } = useI18n()

const advantages = computed(() => [
  {
    id: 1,
    icon: '🚀',
    title: t('about.advantage1.title'),
    description: t('about.advantage1.description')
  },
  {
    id: 2,
    icon: '👥',
    title: t('about.advantage2.title'),
    description: t('about.advantage2.description')
  },
  {
    id: 3,
    icon: '💡',
    title: t('about.advantage3.title'),
    description: t('about.advantage3.description')
  },
  {
    id: 4,
    icon: '📈',
    title: t('about.advantage4.title'),
    description: t('about.advantage4.description')
  }
])
</script>

<style scoped>
.about-page {
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
  max-width: 1200px;
  margin: 0 auto;
  padding: 60px 24px;
}

.about-content {
  display: flex;
  flex-direction: column;
  gap: 60px;
}

.about-section {
  background: #fff;
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.about-section h2 {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 24px;
  color: #1a1a1a;
}

.about-section > p {
  font-size: 16px;
  line-height: 1.8;
  color: #666;
  margin-bottom: 16px;
}

.advantages-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
  margin-top: 30px;
}

.advantage-item {
  text-align: center;
  padding: 30px;
  background: #f8f9fa;
  border-radius: 12px;
  transition: all 0.3s;
}

.advantage-item:hover {
  background: #fff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transform: translateY(-3px);
}

.advantage-icon {
  font-size: 48px;
  margin-bottom: 16px;
}

.advantage-item h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 12px;
  color: #1a1a1a;
}

.advantage-item p {
  color: #666;
  font-size: 14px;
  line-height: 1.6;
}

.contact-info {
  margin-top: 24px;
}

.contact-item {
  padding: 16px 0;
  font-size: 16px;
  color: #333;
  border-bottom: 1px solid #eee;
}

.contact-item:last-child {
  border-bottom: none;
}

.contact-item strong {
  color: #18a058;
  margin-right: 8px;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 32px;
  }

  .about-section {
    padding: 24px;
  }

  .advantages-grid {
    grid-template-columns: 1fr;
  }
}
</style>

