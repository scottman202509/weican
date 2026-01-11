<template>
  <div class="products-page">
    <div class="page-header">
      <h1>{{ $t('products.title') }}</h1>
      <p>{{ $t('products.subtitle') }}</p>
    </div>
    <div class="container">
      <div class="products-list">
        <div
          v-for="product in products"
          :key="product.id"
          class="product-item"
        >
          <div class="product-content">
            <div class="product-icon">{{ product.icon }}</div>
            <h2>{{ product.name }}</h2>
            <p>{{ product.description }}</p>
            <ul class="product-features">
              <li v-for="feature in product.features" :key="feature">{{ feature }}</li>
            </ul>
            <n-button type="primary" @click="handleLearnMore(product)">
              了解更多
            </n-button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { NButton } from 'naive-ui'

const router = useRouter()

const products = ref([
  {
    id: 1,
    name: 'POS系统',
    key: 'pos',
    icon: '💻',
    description: '功能强大的收银管理系统，支持多种支付方式，实时数据同步',
    features: [
      '快速收银结算',
      '多种支付方式',
      '实时数据同步',
      '库存管理',
      '报表分析'
    ]
  },
  {
    id: 2,
    name: '自助点餐机',
    key: 'kiosk',
    icon: '🖥️',
    description: '店内自助点餐终端，减少排队时间，提升顾客体验',
    features: [
      '触摸屏操作',
      '多种语言支持',
      '支付一体化',
      '订单实时同步',
      '数据分析'
    ]
  },
  {
    id: 3,
    name: '在线点餐',
    key: 'online',
    icon: '📱',
    description: '餐厅网站和品牌App，让顾客随时随地在线点餐',
    features: [
      '在线菜单浏览',
      '移动端适配',
      '订单追踪',
      '会员积分',
      '优惠活动'
    ]
  },
  {
    id: 4,
    name: '会员系统',
    key: 'member',
    icon: '🎯',
    description: '完善的会员管理系统，提升客户复购率',
    features: [
      '会员注册管理',
      '积分系统',
      '优惠券发放',
      '会员等级',
      '营销活动'
    ]
  },
  {
    id: 5,
    name: '外卖平台整合',
    key: 'delivery',
    icon: '🚀',
    description: '整合多个外卖平台，统一管理订单',
    features: [
      '多平台对接',
      '订单统一管理',
      '自动接单',
      '库存同步',
      '数据分析'
    ]
  },
  {
    id: 6,
    name: '厨房显示系统',
    key: 'kds',
    icon: '📺',
    description: '厨房订单显示系统，提升出餐效率',
    features: [
      '订单实时显示',
      '出餐提醒',
      '订单分类',
      '时间统计',
      '效率分析'
    ]
  }
])

const handleLearnMore = (product) => {
  if (product.key) {
    router.push(`/product/${product.key}`)
  }
}
</script>

<style scoped>
.products-page {
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

.products-list {
  display: grid;
  gap: 40px;
}

.product-item {
  background: #fff;
  border-radius: 12px;
  padding: 40px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: all 0.3s;
}

.product-item:hover {
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
  transform: translateY(-5px);
}

.product-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.product-icon {
  font-size: 64px;
  margin-bottom: 24px;
}

.product-content h2 {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 16px;
  color: #1a1a1a;
}

.product-content > p {
  font-size: 18px;
  color: #666;
  margin-bottom: 24px;
  line-height: 1.8;
}

.product-features {
  list-style: none;
  margin-bottom: 30px;
  padding-left: 0;
}

.product-features li {
  padding: 8px 0;
  padding-left: 24px;
  position: relative;
  color: #333;
}

.product-features li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: #18a058;
  font-weight: bold;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 32px;
  }

  .product-item {
    padding: 24px;
  }

  .product-content h2 {
    font-size: 24px;
  }
}
</style>

