# 微餐官网

基于 Vue 3 + Naive UI 的餐饮系统公司官网项目，仿照 Chowbus 网站风格设计。

## 技术栈

- Vue 3
- Vue Router
- Naive UI
- Vite

## 项目结构

```
weican/
├── src/
│   ├── components/      # 公共组件
│   │   ├── Header.vue   # 头部导航
│   │   └── Footer.vue   # 页脚
│   ├── views/          # 页面组件
│   │   ├── Home.vue     # 首页
│   │   ├── Products.vue # 产品页面
│   │   ├── Solutions.vue # 解决方案页面
│   │   └── About.vue    # 关于我们
│   ├── router/         # 路由配置
│   │   └── index.js
│   ├── App.vue         # 根组件
│   └── main.js         # 入口文件
├── index.html
├── package.json
└── vite.config.js
```

## 安装和运行

1. 安装依赖：
```bash
npm install
```

2. 启动开发服务器：
```bash
npm run dev
```

3. 构建生产版本：
```bash
npm run build
```

4. 预览生产构建：
```bash
npm run preview
```

## 功能特性

- ✅ 响应式设计，支持移动端和桌面端
- ✅ 现代化的 UI 设计，仿照 Chowbus 风格
- ✅ 多页面路由导航
- ✅ 产品功能展示
- ✅ 餐厅类型解决方案
- ✅ 客户案例展示
- ✅ 完整的页面布局（Header + Footer）

## 页面说明

- **首页** (`/`): 包含 Hero 区域、餐厅类型、产品展示、客户案例等
- **产品功能** (`/products`): 详细的产品功能列表
- **解决方案** (`/solutions`): 不同餐厅类型的解决方案
- **关于我们** (`/about`): 公司简介和联系方式

## 开发说明

项目使用 Vue 3 Composition API 和 Naive UI 组件库构建，所有样式都采用响应式设计，确保在不同设备上都有良好的显示效果。

