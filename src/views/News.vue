<template>
  <div class="news-page">
    <div class="page-header">
      <h1>{{ $t('news.title') }}</h1>
      <p>{{ $t('news.subtitle') }}</p>
    </div>
    <div class="container">
      <div class="news-content">
        <div class="news-grid">
          <div
            v-for="article in articles"
            :key="article.id"
            class="news-card"
            @click="handleArticleClick(article)"
          >
            <div class="news-image">
              <div class="image-placeholder">{{ article.category }}</div>
            </div>
            <div class="news-body">
              <div class="news-meta">
                <span class="category">{{ article.category }}</span>
                <span class="date">{{ article.date }}</span>
              </div>
              <h3>{{ article.title }}</h3>
              <p>{{ article.summary }}</p>
              <span class="read-more">{{ $t('news.readMore') }} →</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useI18n } from 'vue-i18n'

const { t } = useI18n()

const articles = computed(() => [
  {
    id: 1,
    title: t('news.articles.article1.title'),
    summary: t('news.articles.article1.summary'),
    category: t('news.articles.article1.category'),
    categoryKey: 'trend',
    date: '2025-01-15'
  },
  {
    id: 2,
    title: t('news.articles.article2.title'),
    summary: t('news.articles.article2.summary'),
    category: t('news.articles.article2.category'),
    categoryKey: 'management',
    date: '2025-01-12'
  },
  {
    id: 3,
    title: t('news.articles.article3.title'),
    summary: t('news.articles.article3.summary'),
    category: t('news.articles.article3.category'),
    categoryKey: 'marketing',
    date: '2025-01-10'
  },
  {
    id: 4,
    title: t('news.articles.article4.title'),
    summary: t('news.articles.article4.summary'),
    category: t('news.articles.article4.category'),
    categoryKey: 'hardware',
    date: '2025-01-08'
  },
  {
    id: 5,
    title: t('news.articles.article5.title'),
    summary: t('news.articles.article5.summary'),
    category: t('news.articles.article5.category'),
    categoryKey: 'chain',
    date: '2025-01-05'
  },
  {
    id: 6,
    title: t('news.articles.article6.title'),
    summary: t('news.articles.article6.summary'),
    category: t('news.articles.article6.category'),
    categoryKey: 'integration',
    date: '2025-01-03'
  }
])

const handleArticleClick = (article) => {
  console.log('查看文章:', article.title)
}
</script>

<style scoped>
.news-page {
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

.news-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 30px;
}

.news-card {
  background: #fff;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  cursor: pointer;
  transition: all 0.3s;
}

.news-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
}

.news-image {
  width: 100%;
  height: 200px;
  background: linear-gradient(135deg, #18a058 0%, #36ad6a 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.image-placeholder {
  color: #fff;
  font-size: 24px;
  font-weight: 600;
  opacity: 0.8;
}

.news-body {
  padding: 24px;
}

.news-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
  font-size: 14px;
}

.category {
  background: #f0f9ff;
  color: #18a058;
  padding: 4px 12px;
  border-radius: 12px;
  font-weight: 500;
}

.date {
  color: #999;
}

.news-body h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 12px;
  color: #1a1a1a;
  line-height: 1.4;
}

.news-body > p {
  color: #666;
  line-height: 1.6;
  margin-bottom: 16px;
  font-size: 14px;
}

.read-more {
  color: #18a058;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s;
}

.read-more:hover {
  color: #36ad6a;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 32px;
  }

  .news-grid {
    grid-template-columns: 1fr;
  }
}
</style>
