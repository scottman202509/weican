<template>
  <div class="product-detail-page">
    <div class="page-header">
      <h1>{{ productInfo.title }}</h1>
      <p>{{ productInfo.subtitle }}</p>
    </div>
    <div class="container">
      <div class="product-content">
        <div class="product-intro">
          <div class="intro-text">
            <h2>{{ $t('productDetail.intro') }}</h2>
            <p v-for="(para, index) in productInfo.introduction" :key="index">{{ para }}</p>
          </div>
          <div class="intro-image">
            <div class="image-placeholder">{{ productInfo.icon }}</div>
          </div>
        </div>

        <div class="features-section">
          <h2>{{ $t('productDetail.coreFeatures') }}</h2>
          <div class="features-grid">
            <div
              v-for="(feature, index) in productInfo.features"
              :key="index"
              class="feature-item"
            >
              <div class="feature-icon">{{ feature.icon }}</div>
              <h3>{{ feature.title }}</h3>
              <p>{{ feature.description }}</p>
            </div>
          </div>
        </div>

        <div class="benefits-section">
          <h2>{{ $t('productDetail.advantages') }}</h2>
          <div class="benefits-list">
            <div
              v-for="(benefit, index) in productInfo.benefits"
              :key="index"
              class="benefit-item"
            >
              <div class="benefit-number">{{ index + 1 }}</div>
              <div class="benefit-content">
                <h3>{{ benefit.title }}</h3>
                <p>{{ benefit.description }}</p>
              </div>
            </div>
          </div>
        </div>

        <div class="cta-section">
          <n-button type="primary" size="large" @click="handleConsult">
            {{ $t('common.immediately') }}
          </n-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import { useI18n } from 'vue-i18n'
import { NButton } from 'naive-ui'

const route = useRoute()
const router = useRouter()
const { t } = useI18n()

const productInfo = computed(() => {
  const productKey = route.params.id || 'pos'
  const baseKey = `productDetail.${productKey}`
  
  const productMap = {
    pos: {
      title: t(`productDetail.pos.title`),
      subtitle: t(`productDetail.pos.subtitle`),
      icon: '💻',
      introduction: [
        t(`productDetail.pos.intro1`),
        t(`productDetail.pos.intro2`),
        t(`productDetail.pos.intro3`)
      ],
      features: [
        {
          icon: '⚡',
          title: t(`productDetail.pos.feature1.title`),
          description: t(`productDetail.pos.feature1.description`)
        },
        {
          icon: '💳',
          title: t(`productDetail.pos.feature2.title`),
          description: t(`productDetail.pos.feature2.description`)
        },
        {
          icon: '📊',
          title: t(`productDetail.pos.feature3.title`),
          description: t(`productDetail.pos.feature3.description`)
        },
        {
          icon: '📦',
          title: t(`productDetail.pos.feature4.title`),
          description: t(`productDetail.pos.feature4.description`)
        },
        {
          icon: '👥',
          title: t(`productDetail.pos.feature5.title`),
          description: t(`productDetail.pos.feature5.description`)
        },
        {
          icon: '☁️',
          title: t(`productDetail.pos.feature6.title`),
          description: t(`productDetail.pos.feature6.description`)
        }
      ],
      benefits: [
        {
          title: t(`productDetail.pos.benefit1.title`),
          description: t(`productDetail.pos.benefit1.description`)
        },
        {
          title: t(`productDetail.pos.benefit2.title`),
          description: t(`productDetail.pos.benefit2.description`)
        },
        {
          title: t(`productDetail.pos.benefit3.title`),
          description: t(`productDetail.pos.benefit3.description`)
        },
        {
          title: t(`productDetail.pos.benefit4.title`),
          description: t(`productDetail.pos.benefit4.description`)
        }
      ]
    },
    kiosk: {
      title: t(`productDetail.kiosk.title`),
      subtitle: t(`productDetail.kiosk.subtitle`),
      icon: '🖥️',
      introduction: [
        t(`productDetail.kiosk.intro1`),
        t(`productDetail.kiosk.intro2`),
        t(`productDetail.kiosk.intro3`)
      ],
      features: [
        {
          icon: '👆',
          title: t(`productDetail.kiosk.feature1.title`),
          description: t(`productDetail.kiosk.feature1.description`)
        },
        {
          icon: '🌐',
          title: t(`productDetail.kiosk.feature2.title`),
          description: t(`productDetail.kiosk.feature2.description`)
        },
        {
          icon: '💳',
          title: t(`productDetail.kiosk.feature3.title`),
          description: t(`productDetail.kiosk.feature3.description`)
        },
        {
          icon: '🔄',
          title: t(`productDetail.kiosk.feature4.title`),
          description: t(`productDetail.kiosk.feature4.description`)
        },
        {
          icon: '📱',
          title: t(`productDetail.kiosk.feature5.title`),
          description: t(`productDetail.kiosk.feature5.description`)
        },
        {
          icon: '📈',
          title: t(`productDetail.kiosk.feature6.title`),
          description: t(`productDetail.kiosk.feature6.description`)
        }
      ],
      benefits: [
        {
          title: t(`productDetail.kiosk.benefit1.title`),
          description: t(`productDetail.kiosk.benefit1.description`)
        },
        {
          title: t(`productDetail.kiosk.benefit2.title`),
          description: t(`productDetail.kiosk.benefit2.description`)
        },
        {
          title: t(`productDetail.kiosk.benefit3.title`),
          description: t(`productDetail.kiosk.benefit3.description`)
        },
        {
          title: t(`productDetail.kiosk.benefit4.title`),
          description: t(`productDetail.kiosk.benefit4.description`)
        }
      ]
    },
    online: {
      title: t(`productDetail.online.title`),
      subtitle: t(`productDetail.online.subtitle`),
      icon: '📱',
      introduction: [
        t(`productDetail.online.intro1`),
        t(`productDetail.online.intro2`),
        t(`productDetail.online.intro3`)
      ],
      features: [
        {
          icon: '🍽️',
          title: t(`productDetail.online.feature1.title`),
          description: t(`productDetail.online.feature1.description`)
        },
        {
          icon: '📱',
          title: t(`productDetail.online.feature2.title`),
          description: t(`productDetail.online.feature2.description`)
        },
        {
          icon: '📍',
          title: t(`productDetail.online.feature3.title`),
          description: t(`productDetail.online.feature3.description`)
        },
        {
          icon: '🎁',
          title: t(`productDetail.online.feature4.title`),
          description: t(`productDetail.online.feature4.description`)
        },
        {
          icon: '🎉',
          title: t(`productDetail.online.feature5.title`),
          description: t(`productDetail.online.feature5.description`)
        },
        {
          icon: '💬',
          title: t(`productDetail.online.feature6.title`),
          description: t(`productDetail.online.feature6.description`)
        }
      ],
      benefits: [
        {
          title: t(`productDetail.online.benefit1.title`),
          description: t(`productDetail.online.benefit1.description`)
        },
        {
          title: t(`productDetail.online.benefit2.title`),
          description: t(`productDetail.online.benefit2.description`)
        },
        {
          title: t(`productDetail.online.benefit3.title`),
          description: t(`productDetail.online.benefit3.description`)
        },
        {
          title: t(`productDetail.online.benefit4.title`),
          description: t(`productDetail.online.benefit4.description`)
        }
      ]
    },
    member: {
      title: t(`productDetail.member.title`),
      subtitle: t(`productDetail.member.subtitle`),
      icon: '🎯',
      introduction: [
        t(`productDetail.member.intro1`),
        t(`productDetail.member.intro2`),
        t(`productDetail.member.intro3`)
      ],
      features: [
        {
          icon: '👤',
          title: t(`productDetail.member.feature1.title`),
          description: t(`productDetail.member.feature1.description`)
        },
        {
          icon: '⭐',
          title: t(`productDetail.member.feature2.title`),
          description: t(`productDetail.member.feature2.description`)
        },
        {
          icon: '🎫',
          title: t(`productDetail.member.feature3.title`),
          description: t(`productDetail.member.feature3.description`)
        },
        {
          icon: '🏆',
          title: t(`productDetail.member.feature4.title`),
          description: t(`productDetail.member.feature4.description`)
        },
        {
          icon: '📢',
          title: t(`productDetail.member.feature5.title`),
          description: t(`productDetail.member.feature5.description`)
        },
        {
          icon: '📊',
          title: t(`productDetail.member.feature6.title`),
          description: t(`productDetail.member.feature6.description`)
        }
      ],
      benefits: [
        {
          title: t(`productDetail.member.benefit1.title`),
          description: t(`productDetail.member.benefit1.description`)
        },
        {
          title: t(`productDetail.member.benefit2.title`),
          description: t(`productDetail.member.benefit2.description`)
        },
        {
          title: t(`productDetail.member.benefit3.title`),
          description: t(`productDetail.member.benefit3.description`)
        },
        {
          title: t(`productDetail.member.benefit4.title`),
          description: t(`productDetail.member.benefit4.description`)
        }
      ]
    }
  }
  
  return productMap[productKey] || productMap.pos
})

const handleConsult = () => {
  router.push('/contact')
}
</script>

<style scoped>
.product-detail-page {
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

.product-intro {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  margin-bottom: 80px;
  align-items: center;
}

.intro-text h2 {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 24px;
  color: #1a1a1a;
}

.intro-text p {
  font-size: 16px;
  line-height: 1.8;
  color: #666;
  margin-bottom: 16px;
}

.intro-image {
  display: flex;
  align-items: center;
  justify-content: center;
}

.image-placeholder {
  font-size: 120px;
  background: #f8f9fa;
  width: 100%;
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
}

.features-section,
.benefits-section {
  margin-bottom: 80px;
}

.features-section h2,
.benefits-section h2 {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 40px;
  color: #1a1a1a;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
}

.feature-item {
  background: #f8f9fa;
  padding: 30px;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s;
}

.feature-item:hover {
  background: #fff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transform: translateY(-3px);
}

.feature-icon {
  font-size: 48px;
  margin-bottom: 16px;
}

.feature-item h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 12px;
  color: #1a1a1a;
}

.feature-item p {
  color: #666;
  font-size: 14px;
  line-height: 1.6;
}

.benefits-list {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.benefit-item {
  display: flex;
  gap: 24px;
  background: #fff;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: all 0.3s;
}

.benefit-item:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
  transform: translateX(5px);
}

.benefit-number {
  width: 50px;
  height: 50px;
  background: #18a058;
  color: #fff;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  font-weight: 700;
  flex-shrink: 0;
}

.benefit-content h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 8px;
  color: #1a1a1a;
}

.benefit-content p {
  color: #666;
  line-height: 1.6;
}

.cta-section {
  text-align: center;
  padding: 40px 0;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 32px;
  }

  .product-intro {
    grid-template-columns: 1fr;
  }

  .features-grid {
    grid-template-columns: 1fr;
  }
}
</style>
