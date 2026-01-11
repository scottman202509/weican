<template>
  <div class="solution-detail-page">
    <div class="page-header">
      <h1>{{ solutionInfo.title }}</h1>
      <p>{{ solutionInfo.subtitle }}</p>
    </div>
    <div class="container">
      <div class="solution-content">
        <div class="solution-intro">
          <div class="intro-text">
            <h2>{{ $t('solutionDetail.intro') }}</h2>
            <p v-for="(para, index) in solutionInfo.introduction" :key="index">{{ para }}</p>
          </div>
          <div class="intro-image">
            <div class="image-placeholder">{{ solutionInfo.icon }}</div>
          </div>
        </div>

        <div class="features-section">
          <h2>{{ $t('solutionDetail.coreFeatures') }}</h2>
          <div class="features-grid">
            <div
              v-for="(feature, index) in solutionInfo.features"
              :key="index"
              class="feature-item"
            >
              <div class="feature-icon">{{ feature.icon }}</div>
              <h3>{{ feature.title }}</h3>
              <p>{{ feature.description }}</p>
            </div>
          </div>
        </div>

        <div class="scenarios-section">
          <h2>{{ $t('solutionDetail.scenarios') }}</h2>
          <div class="scenarios-list">
            <div
              v-for="(scenario, index) in solutionInfo.scenarios"
              :key="index"
              class="scenario-item"
            >
              <div class="scenario-icon">✓</div>
              <p>{{ scenario }}</p>
            </div>
          </div>
        </div>

        <div class="benefits-section">
          <h2>{{ $t('solutionDetail.advantages') }}</h2>
          <div class="benefits-grid">
            <div
              v-for="(benefit, index) in solutionInfo.benefits"
              :key="index"
              class="benefit-card"
            >
              <h3>{{ benefit.title }}</h3>
              <p>{{ benefit.description }}</p>
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

const solutionInfo = computed(() => {
  const solutionKey = route.params.id || 'fast'
  const baseKey = `solutionDetail.${solutionKey}`
  
  const solutionMap = {
    fast: {
      title: t(`solutionDetail.fast.title`),
      subtitle: t(`solutionDetail.fast.subtitle`),
      icon: '🍔',
      introduction: [
        t(`solutionDetail.fast.intro1`),
        t(`solutionDetail.fast.intro2`),
        t(`solutionDetail.fast.intro3`)
      ],
      features: [
        {
          icon: '⚡',
          title: t(`solutionDetail.fast.feature1.title`),
          description: t(`solutionDetail.fast.feature1.description`)
        },
        {
          icon: '💳',
          title: t(`solutionDetail.fast.feature2.title`),
          description: t(`solutionDetail.fast.feature2.description`)
        },
        {
          icon: '📺',
          title: t(`solutionDetail.fast.feature3.title`),
          description: t(`solutionDetail.fast.feature3.description`)
        },
        {
          icon: '📦',
          title: t(`solutionDetail.fast.feature4.title`),
          description: t(`solutionDetail.fast.feature4.description`)
        },
        {
          icon: '📊',
          title: t(`solutionDetail.fast.feature5.title`),
          description: t(`solutionDetail.fast.feature5.description`)
        },
        {
          icon: '🎯',
          title: t(`solutionDetail.fast.feature6.title`),
          description: t(`solutionDetail.fast.feature6.description`)
        }
      ],
      scenarios: [
        t(`solutionDetail.fast.scenario1`),
        t(`solutionDetail.fast.scenario2`),
        t(`solutionDetail.fast.scenario3`),
        t(`solutionDetail.fast.scenario4`)
      ],
      benefits: [
        {
          title: t(`solutionDetail.fast.benefit1.title`),
          description: t(`solutionDetail.fast.benefit1.description`)
        },
        {
          title: t(`solutionDetail.fast.benefit2.title`),
          description: t(`solutionDetail.fast.benefit2.description`)
        },
        {
          title: t(`solutionDetail.fast.benefit3.title`),
          description: t(`solutionDetail.fast.benefit3.description`)
        },
        {
          title: t(`solutionDetail.fast.benefit4.title`),
          description: t(`solutionDetail.fast.benefit4.description`)
        }
      ]
    },
    'dine-in': {
      title: t(`solutionDetail.dineIn.title`),
      subtitle: t(`solutionDetail.dineIn.subtitle`),
      icon: '🍽️',
      introduction: [
        t(`solutionDetail.dineIn.intro1`),
        t(`solutionDetail.dineIn.intro2`),
        t(`solutionDetail.dineIn.intro3`)
      ],
      features: [
        {
          icon: '🪑',
          title: t(`solutionDetail.dineIn.feature1.title`),
          description: t(`solutionDetail.dineIn.feature1.description`)
        },
        {
          icon: '👨‍💼',
          title: t(`solutionDetail.dineIn.feature2.title`),
          description: t(`solutionDetail.dineIn.feature2.description`)
        },
        {
          icon: '📅',
          title: t(`solutionDetail.dineIn.feature3.title`),
          description: t(`solutionDetail.dineIn.feature3.description`)
        },
        {
          icon: '👥',
          title: t(`solutionDetail.dineIn.feature4.title`),
          description: t(`solutionDetail.dineIn.feature4.description`)
        },
        {
          icon: '💳',
          title: t(`solutionDetail.dineIn.feature5.title`),
          description: t(`solutionDetail.dineIn.feature5.description`)
        },
        {
          icon: '📊',
          title: t(`solutionDetail.dineIn.feature6.title`),
          description: t(`solutionDetail.dineIn.feature6.description`)
        }
      ],
      scenarios: [
        t(`solutionDetail.dineIn.scenario1`),
        t(`solutionDetail.dineIn.scenario2`),
        t(`solutionDetail.dineIn.scenario3`),
        t(`solutionDetail.dineIn.scenario4`)
      ],
      benefits: [
        {
          title: t(`solutionDetail.dineIn.benefit1.title`),
          description: t(`solutionDetail.dineIn.benefit1.description`)
        },
        {
          title: t(`solutionDetail.dineIn.benefit2.title`),
          description: t(`solutionDetail.dineIn.benefit2.description`)
        },
        {
          title: t(`solutionDetail.dineIn.benefit3.title`),
          description: t(`solutionDetail.dineIn.benefit3.description`)
        },
        {
          title: t(`solutionDetail.dineIn.benefit4.title`),
          description: t(`solutionDetail.dineIn.benefit4.description`)
        }
      ]
    },
    tea: {
      title: t(`solutionDetail.tea.title`),
      subtitle: t(`solutionDetail.tea.subtitle`),
      icon: '🧋',
      introduction: [
        t(`solutionDetail.tea.intro1`),
        t(`solutionDetail.tea.intro2`),
        t(`solutionDetail.tea.intro3`)
      ],
      features: [
        {
          icon: '⚡',
          title: t(`solutionDetail.tea.feature1.title`),
          description: t(`solutionDetail.tea.feature1.description`)
        },
        {
          icon: '🎨',
          title: t(`solutionDetail.tea.feature2.title`),
          description: t(`solutionDetail.tea.feature2.description`)
        },
        {
          icon: '⭐',
          title: t(`solutionDetail.tea.feature3.title`),
          description: t(`solutionDetail.tea.feature3.description`)
        },
        {
          icon: '🎫',
          title: t(`solutionDetail.tea.feature4.title`),
          description: t(`solutionDetail.tea.feature4.description`)
        },
        {
          icon: '📱',
          title: t(`solutionDetail.tea.feature5.title`),
          description: t(`solutionDetail.tea.feature5.description`)
        },
        {
          icon: '📊',
          title: t(`solutionDetail.tea.feature6.title`),
          description: t(`solutionDetail.tea.feature6.description`)
        }
      ],
      scenarios: [
        t(`solutionDetail.tea.scenario1`),
        t(`solutionDetail.tea.scenario2`),
        t(`solutionDetail.tea.scenario3`),
        t(`solutionDetail.tea.scenario4`)
      ],
      benefits: [
        {
          title: t(`solutionDetail.tea.benefit1.title`),
          description: t(`solutionDetail.tea.benefit1.description`)
        },
        {
          title: t(`solutionDetail.tea.benefit2.title`),
          description: t(`solutionDetail.tea.benefit2.description`)
        },
        {
          title: t(`solutionDetail.tea.benefit3.title`),
          description: t(`solutionDetail.tea.benefit3.description`)
        },
        {
          title: t(`solutionDetail.tea.benefit4.title`),
          description: t(`solutionDetail.tea.benefit4.description`)
        }
      ]
    },
    hotpot: {
      title: t(`solutionDetail.hotpot.title`),
      subtitle: t(`solutionDetail.hotpot.subtitle`),
      icon: '🍲',
      introduction: [
        t(`solutionDetail.hotpot.intro1`),
        t(`solutionDetail.hotpot.intro2`),
        t(`solutionDetail.hotpot.intro3`)
      ],
      features: [
        {
          icon: '⏱️',
          title: t(`solutionDetail.hotpot.feature1.title`),
          description: t(`solutionDetail.hotpot.feature1.description`)
        },
        {
          icon: '🪑',
          title: t(`solutionDetail.hotpot.feature2.title`),
          description: t(`solutionDetail.hotpot.feature2.description`)
        },
        {
          icon: '👥',
          title: t(`solutionDetail.hotpot.feature3.title`),
          description: t(`solutionDetail.hotpot.feature3.description`)
        },
        {
          icon: '🍲',
          title: t(`solutionDetail.hotpot.feature4.title`),
          description: t(`solutionDetail.hotpot.feature4.description`)
        },
        {
          icon: '👥',
          title: t(`solutionDetail.hotpot.feature5.title`),
          description: t(`solutionDetail.hotpot.feature5.description`)
        },
        {
          icon: '📊',
          title: t(`solutionDetail.hotpot.feature6.title`),
          description: t(`solutionDetail.hotpot.feature6.description`)
        }
      ],
      scenarios: [
        t(`solutionDetail.hotpot.scenario1`),
        t(`solutionDetail.hotpot.scenario2`),
        t(`solutionDetail.hotpot.scenario3`),
        t(`solutionDetail.hotpot.scenario4`)
      ],
      benefits: [
        {
          title: t(`solutionDetail.hotpot.benefit1.title`),
          description: t(`solutionDetail.hotpot.benefit1.description`)
        },
        {
          title: t(`solutionDetail.hotpot.benefit2.title`),
          description: t(`solutionDetail.hotpot.benefit2.description`)
        },
        {
          title: t(`solutionDetail.hotpot.benefit3.title`),
          description: t(`solutionDetail.hotpot.benefit3.description`)
        },
        {
          title: t(`solutionDetail.hotpot.benefit4.title`),
          description: t(`solutionDetail.hotpot.benefit4.description`)
        }
      ]
    }
  }
  
  return solutionMap[solutionKey] || solutionMap.fast
})

const handleConsult = () => {
  router.push('/contact')
}
</script>

<style scoped>
.solution-detail-page {
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

.solution-intro {
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
.scenarios-section,
.benefits-section {
  margin-bottom: 80px;
}

.features-section h2,
.scenarios-section h2,
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

.scenarios-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.scenario-item {
  display: flex;
  align-items: center;
  gap: 12px;
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.scenario-icon {
  width: 24px;
  height: 24px;
  background: #18a058;
  color: #fff;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  flex-shrink: 0;
}

.scenario-item p {
  color: #333;
  margin: 0;
}

.benefits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
}

.benefit-card {
  background: #fff;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: all 0.3s;
}

.benefit-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
  transform: translateY(-3px);
}

.benefit-card h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 12px;
  color: #1a1a1a;
}

.benefit-card p {
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

  .solution-intro {
    grid-template-columns: 1fr;
  }

  .features-grid,
  .benefits-grid {
    grid-template-columns: 1fr;
  }
}
</style>
