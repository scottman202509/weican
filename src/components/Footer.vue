<template>
  <n-layout-footer class="footer">
    <div class="footer-content">
      <div class="footer-section">
        <h3>{{ $t('footer.products') }}</h3>
        <ul>
          <li><a href="#" @click.prevent="handleLinkClick('/products')">{{ $t('footer.posManagement') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/product/kiosk')">{{ $t('footer.kiosk') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/product/online')">{{ $t('footer.onlineOrdering') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/products')">{{ $t('footer.deliveryIntegration') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/product/member')">{{ $t('footer.memberSystem') }}</a></li>
        </ul>
      </div>
      <div class="footer-section">
        <h3>{{ $t('footer.solutions') }}</h3>
        <ul>
          <li><a href="#" @click.prevent="handleLinkClick('/solution/dine-in')">{{ $t('footer.dineInRestaurant') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/solution/fast')">{{ $t('footer.fastRestaurant') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/solutions')">{{ $t('footer.newRestaurant') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/solutions')">{{ $t('footer.switchToWeican') }}</a></li>
        </ul>
      </div>
      <div class="footer-section">
        <h3>{{ $t('footer.pricing') }}</h3>
        <ul>
          <li><a href="#" @click.prevent="handleLinkClick('/pricing')">{{ $t('footer.pricePlan') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/pricing')">{{ $t('footer.whyChooseWeican') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/contact')">{{ $t('footer.contactUs') }}</a></li>
        </ul>
      </div>
      <div class="footer-section">
        <h3>{{ $t('footer.resources') }}</h3>
        <ul>
          <li><a href="#" @click.prevent="handleLinkClick('/about')">{{ $t('footer.aboutUs') }}</a></li>
          <li><a href="#" @click.prevent="handleLinkClick('/news')">{{ $t('footer.news') }}</a></li>
          <li>{{ $t('footer.joinUs') }}</li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <p>{{ $t('footer.copyright') }}</p>
    </div>
  </n-layout-footer>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { useI18n } from 'vue-i18n'
import { NLayoutFooter } from 'naive-ui'

const router = useRouter()
const { t } = useI18n()

const handleLinkClick = (path) => {
  if (path) {
    router.push(path)
  }
}
</script>

<style scoped>
.footer {
  background: #1a1a1a;
  color: #fff;
  padding: 60px 24px 24px;
  margin-top: auto;
}

.footer-content {
  max-width: 1400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 40px;
  margin-bottom: 40px;
}

.footer-section h3 {
  color: #fff;
  margin-bottom: 20px;
  font-size: 16px;
  font-weight: 600;
}

.footer-section ul {
  list-style: none;
}

.footer-section ul li {
  margin-bottom: 12px;
}

.footer-section ul li a {
  color: #999;
  text-decoration: none;
  transition: color 0.3s;
}

.footer-section ul li a:hover {
  color: #18a058;
}

.footer-bottom {
  max-width: 1400px;
  margin: 0 auto;
  padding-top: 24px;
  border-top: 1px solid #333;
  text-align: center;
}

.footer-bottom p {
  color: #666;
  font-size: 14px;
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
  }
}
</style>

