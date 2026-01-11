<template>
  <div class="contact-page">
    <div class="page-header">
      <h1>{{ $t('contact.title') }}</h1>
      <p>{{ $t('contact.subtitle') }}</p>
    </div>
    <div class="container">
      <div class="contact-content">
        <div class="contact-grid">
          <div class="contact-form-section">
            <h2>{{ $t('contact.formTitle') }}</h2>
            <p class="form-description">
              {{ $t('contact.formDesc') }}
            </p>
            <n-form
              ref="formRef"
              :model="formData"
              :rules="rules"
              label-placement="left"
              label-width="100"
              size="large"
            >
              <n-form-item :label="$t('common.name')" path="name">
                <n-input v-model:value="formData.name" :placeholder="$t('common.name')" />
              </n-form-item>
              <n-form-item :label="$t('common.phone')" path="phone">
                <n-input v-model:value="formData.phone" :placeholder="$t('common.phone')" />
              </n-form-item>
              <n-form-item :label="$t('common.email')" path="email">
                <n-input v-model:value="formData.email" :placeholder="$t('common.email')" />
              </n-form-item>
              <n-form-item :label="$t('contact.restaurantName')" path="restaurant">
                <n-input v-model:value="formData.restaurant" :placeholder="$t('contact.restaurantName')" />
              </n-form-item>
              <n-form-item :label="$t('contact.restaurantType')" path="type">
                <n-select
                  v-model:value="formData.type"
                  :placeholder="$t('contact.restaurantType')"
                  :options="restaurantTypes"
                />
              </n-form-item>
              <n-form-item :label="$t('common.message')" path="message">
                <n-input
                  v-model:value="formData.message"
                  type="textarea"
                  :placeholder="$t('common.message')"
                  :rows="4"
                />
              </n-form-item>
              <n-form-item>
                <n-button type="primary" size="large" block @click="handleSubmit">
                  {{ $t('contact.submitConsult') }}
                </n-button>
              </n-form-item>
            </n-form>
          </div>

          <div class="contact-info-section">
            <h2>{{ $t('contact.contactInfo') }}</h2>
            <div class="info-list">
              <div class="info-item">
                <div class="info-icon">📧</div>
                <div class="info-content">
                  <h3>邮箱</h3>
                  <p>contact@weican.com</p>
                </div>
              </div>
              <div class="info-item">
                <div class="info-icon">📞</div>
                <div class="info-content">
                  <h3>电话</h3>
                  <p>+81 0120046042</p>
                </div>
              </div>
              <div class="info-item">
                <div class="info-icon">📍</div>
                <div class="info-content">
                  <h3>地址</h3>
                  <p>〒540-0012 Osaka, Chuo Ward, Tanimachi, 2 Chome−9−3 ザ・ファインタワー大手前 １Ｆ</p>
                </div>
              </div>
              <div class="info-item">
                <div class="info-icon">🕒</div>
                <div class="info-content">
                  <h3>{{ $t('contact.workingHours') }}</h3>
                  <p>{{ $t('contact.workingHoursWeekday') }}</p>
                  <p>{{ $t('contact.workingHoursWeekend') }}</p>
                </div>
              </div>
            </div>

            <div class="why-contact">
              <h3>{{ $t('contact.whyContact') }}</h3>
              <ul>
                <li>✓ {{ $t('contact.whyContact1') }}</li>
                <li>✓ {{ $t('contact.whyContact2') }}</li>
                <li>✓ {{ $t('contact.whyContact3') }}</li>
                <li>✓ {{ $t('contact.whyContact4') }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useI18n } from 'vue-i18n'
import { NForm, NFormItem, NInput, NButton, NSelect, useMessage } from 'naive-ui'

const { t } = useI18n()
const message = useMessage()
const formRef = ref(null)

const formData = ref({
  name: '',
  phone: '',
  email: '',
  restaurant: '',
  type: null,
  message: ''
})

const restaurantTypes = [
  { label: '快餐厅', value: 'fast' },
  { label: '堂食餐厅', value: 'dine-in' },
  { label: '奶茶店', value: 'tea' },
  { label: '火锅店', value: 'hotpot' },
  { label: '自助餐厅', value: 'buffet' },
  { label: '其他', value: 'other' }
]

const rules = {
  name: [
    { required: true, message: '请输入姓名', trigger: 'blur' }
  ],
  phone: [
    { required: true, message: '请输入联系电话', trigger: 'blur' },
    { pattern: /^1[3-9]\d{9}$/, message: '请输入正确的手机号码', trigger: 'blur' }
  ],
  email: [
    { required: true, message: '请输入邮箱', trigger: 'blur' },
    { type: 'email', message: '请输入正确的邮箱地址', trigger: 'blur' }
  ]
}

const handleSubmit = () => {
  formRef.value?.validate((errors) => {
    if (!errors) {
      message.success(t('contact.submitSuccess'))
      // 重置表单
      formData.value = {
        name: '',
        phone: '',
        email: '',
        restaurant: '',
        type: null,
        message: ''
      }
    } else {
      message.error(t('contact.submitError'))
    }
  })
}
</script>

<style scoped>
.contact-page {
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

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  max-width: 1200px;
  margin: 0 auto;
}

.contact-form-section h2,
.contact-info-section h2 {
  font-size: 28px;
  font-weight: 700;
  margin-bottom: 16px;
  color: #1a1a1a;
}

.form-description {
  color: #666;
  margin-bottom: 30px;
  line-height: 1.6;
}

.contact-info-section {
  background: #f8f9fa;
  padding: 40px;
  border-radius: 12px;
}

.info-list {
  margin-bottom: 40px;
}

.info-item {
  display: flex;
  gap: 20px;
  margin-bottom: 30px;
  align-items: flex-start;
}

.info-icon {
  font-size: 32px;
  flex-shrink: 0;
}

.info-content h3 {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 8px;
  color: #1a1a1a;
}

.info-content p {
  color: #666;
  line-height: 1.6;
  margin: 0;
}

.why-contact {
  background: #fff;
  padding: 24px;
  border-radius: 8px;
}

.why-contact h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 16px;
  color: #1a1a1a;
}

.why-contact ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.why-contact ul li {
  padding: 8px 0;
  color: #333;
  font-size: 15px;
}

@media (max-width: 968px) {
  .contact-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .page-header h1 {
    font-size: 32px;
  }
}
</style>
