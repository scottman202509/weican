<template>
  <div class="solutions-page">
    <div class="page-header">
      <h1>{{ $t('solutions.title') }}</h1>
      <p>{{ $t('solutions.subtitle') }}</p>
    </div>
    <div class="container">
      <div class="solutions-grid">
        <div
          v-for="solution in solutions"
          :key="solution.id"
          class="solution-card"
          @click="handleSolutionClick(solution)"
        >
          <div class="solution-icon">{{ solution.icon }}</div>
          <h2>{{ solution.name }}</h2>
          <p>{{ solution.description }}</p>
          <div class="solution-features">
            <span
              v-for="feature in solution.features"
              :key="feature"
              class="feature-tag"
            >
              {{ feature }}
            </span>
          </div>
          <span class="learn-more">查看详情 →</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const solutions = ref([
  {
    id: 1,
    name: '快餐厅',
    key: 'fast',
    icon: '🍔',
    description: '快速高效的点餐收银解决方案',
    features: ['快速点餐', '自助点餐', '快速结算']
  },
  {
    id: 2,
    name: '堂食餐厅',
    key: 'dine-in',
    icon: '🍽️',
    description: '完整的餐厅管理系统',
    features: ['桌台管理', '服务员点餐', '会员系统']
  },
  {
    id: 3,
    name: '奶茶店&甜品店',
    key: 'tea',
    icon: '🧋',
    description: '专业的饮品店解决方案',
    features: ['快速出单', '口味定制', '会员营销']
  },
  {
    id: 4,
    name: '火锅店',
    key: 'hotpot',
    icon: '🍲',
    description: '适合火锅店的特色功能',
    features: ['计时管理', '桌台管理', '多人点餐']
  },
  {
    id: 5,
    name: 'AYCE自助餐厅',
    key: 'buffet',
    icon: '🍱',
    description: '自助餐厅专用系统',
    features: ['计时计费', '人数管理', '会员优惠']
  },
  {
    id: 6,
    name: '韩料店',
    key: 'korean',
    icon: '🍜',
    description: '韩式餐厅定制方案',
    features: ['特色菜单', '套餐管理', '会员系统']
  },
  {
    id: 7,
    name: '日料店',
    key: 'japanese',
    icon: '🍣',
    description: '日式料理店解决方案',
    features: ['精致菜单', '套餐组合', '会员营销']
  },
  {
    id: 8,
    name: '东南亚餐厅',
    key: 'southeast',
    icon: '🍛',
    description: '东南亚风味餐厅系统',
    features: ['特色菜品', '口味管理', '会员系统']
  }
])

const handleSolutionClick = (solution) => {
  if (solution.key) {
    router.push(`/solution/${solution.key}`)
  }
}
</script>

<style scoped>
.solutions-page {
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

.solutions-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}

.solution-card {
  background: #fff;
  padding: 40px 30px;
  border-radius: 12px;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.solution-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
}

.solution-icon {
  font-size: 64px;
  margin-bottom: 24px;
}

.solution-card h2 {
  font-size: 28px;
  font-weight: 700;
  margin-bottom: 16px;
  color: #1a1a1a;
}

.solution-card > p {
  color: #666;
  margin-bottom: 24px;
  font-size: 16px;
  line-height: 1.6;
}

.solution-features {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  justify-content: center;
  margin-bottom: 24px;
}

.feature-tag {
  background: #f0f9ff;
  color: #18a058;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: 500;
}

.learn-more {
  color: #18a058;
  text-decoration: none;
  font-weight: 600;
  transition: color 0.3s;
}

.learn-more:hover {
  color: #36ad6a;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 32px;
  }

  .solutions-grid {
    grid-template-columns: 1fr;
  }
}
</style>

