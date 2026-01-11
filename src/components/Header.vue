<template>
  <n-layout-header bordered class="header">
    <div class="header-content">
      <div class="logo" @click="$router.push('/')">
        <h2>{{ $t('common.brandName') }}</h2>
      </div>
      <n-menu
        v-model:value="activeKey"
        mode="horizontal"
        :options="menuOptions"
        class="nav-menu"
        @update:value="handleMenuSelect"
      />
      <div class="header-actions">
        <n-select
          v-model:value="currentLocale"
          :options="localeOptions"
          size="small"
          class="language-selector"
          @update:value="handleLocaleChange"
        />
        <n-button type="primary" @click="handleContact">{{ $t('common.contact') }}</n-button>
      </div>
    </div>
  </n-layout-header>
</template>

<script setup>
import { ref, watch, computed } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import { useI18n } from 'vue-i18n'
import { NLayoutHeader, NMenu, NButton, NSelect } from 'naive-ui'

const router = useRouter()
const route = useRoute()
const { t, locale } = useI18n()
const activeKey = ref(route.name || 'Home')
const currentLocale = ref(locale.value || 'ja')

const localeOptions = [
  { label: '中文', value: 'zh' },
  { label: 'English', value: 'en' },
  { label: '日本語', value: 'ja' },
  { label: 'ไทย', value: 'th' }
]

watch(() => route.name, (newName) => {
  activeKey.value = newName
})

const menuOptions = computed(() => [
  {
    label: t('header.products'),
    key: 'Products',
    children: [
      { label: t('header.productItems.pos'), key: 'pos', path: '/product/pos' },
      { label: t('header.productItems.kiosk'), key: 'kiosk', path: '/product/kiosk' },
      { label: t('header.productItems.online'), key: 'online', path: '/product/online' },
      { label: t('header.productItems.member'), key: 'member', path: '/product/member' }
    ]
  },
  {
    label: t('header.solutions'),
    key: 'Solutions',
    children: [
      { label: t('header.solutionItems.fast'), key: 'fast', path: '/solution/fast' },
      { label: t('header.solutionItems.dine-in'), key: 'dine-in', path: '/solution/dine-in' },
      { label: t('header.solutionItems.tea'), key: 'tea', path: '/solution/tea' },
      { label: t('header.solutionItems.hotpot'), key: 'hotpot', path: '/solution/hotpot' }
    ]
  },
  {
    label: t('header.pricing'),
    key: 'Pricing',
    path: '/pricing'
  },
  {
    label: t('header.resources'),
    key: 'resources',
    children: [
      { label: t('header.news'), key: 'news', path: '/news' },
      { label: t('header.about'), key: 'About', path: '/about' }
    ]
  }
])

const handleLocaleChange = (value) => {
  locale.value = value
  localStorage.setItem('locale', value)
}

const handleMenuSelect = (key) => {
  // 查找菜单项对应的路径
  const findPath = (options, targetKey) => {
    for (const option of options) {
      if (option.key === targetKey) {
        return option.path
      }
      if (option.children) {
        for (const child of option.children) {
          if (child.key === targetKey) {
            return child.path
          }
        }
      }
    }
    return null
  }

  const path = findPath(menuOptions.value, key)
  if (path) {
    router.push(path)
  } else if (key === 'Products') {
    router.push('/products')
  } else if (key === 'Solutions') {
    router.push('/solutions')
  } else if (key === 'Pricing') {
    router.push('/pricing')
  }
}

const handleContact = () => {
  router.push('/contact')
}
</script>

<style scoped>
.header {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: #fff;
  height: 70px;
}

.header-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 24px;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  cursor: pointer;
  margin-right: 40px;
}

.logo h2 {
  color: #18a058;
  font-size: 24px;
  font-weight: 700;
}

.nav-menu {
  flex: 1;
}

.header-actions {
  display: flex;
  gap: 12px;
  margin-left: 24px;
  align-items: center;
}

.language-selector {
  width: 120px;
}

@media (max-width: 768px) {
  .header-content {
    padding: 0 16px;
  }
  
  .nav-menu {
    display: none;
  }
}
</style>

