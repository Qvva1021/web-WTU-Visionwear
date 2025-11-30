# VisionWear - AI时尚图像生成平台

[功能特性](#-核心功能) • [技术架构](#-技术架构) • [快速开始](#-快速开始) • [部署指南](#-部署指南)


---

## 📖 项目简介

VisionWear 是一个集成了多种AI图像生成技术的时尚设计平台，致力于将前沿AI技术与时尚设计完美融合。平台提供多样化的图像生成能力，包括文本生成图像、风格转换、线稿成图、局部重绘等功能，同时构建了完整的用户社区生态，让用户可以创作、分享和交流时尚设计作品。

### ✨ 项目特色

- 🎨 **多样化AI生成能力**：集成Stable Diffusion、腾讯云AI、阿里云百炼、火山引擎等多种AI模型
- 🏗️ **微服务架构**：采用Spring Cloud微服务架构，模块化设计，易于扩展和维护
- 🎯 **完整业务闭环**：从图像生成到社区分享，提供完整的用户体验
- 🔒 **安全可靠**：JWT认证、权限控制、数据加密等多重安全保障
- 📱 **现代化前端**：基于Vue 3 + Element Plus，响应式设计，用户体验优秀

---

## 🏗️ 技术架构

### 系统架构图

```
┌─────────────────┐
│   Vue 3 前端     │
└────────┬────────┘
         │
┌────────▼────────┐
│  Gateway 网关    │ (统一入口、路由、认证)
└────────┬────────┘
         │
    ┌────┴────┬──────────┬─────────────┐
    │         │          │             │
┌───▼───┐ ┌──▼───┐ ┌───▼────┐ ┌──────▼────┐
│ User  │ │Image │ │Community│ │  Common   │
│ 服务  │ │ 服务 │ │  服务   │ │  公共模块  │
└───┬───┘ └──┬───┘ └───┬────┘ └───────────┘
    │        │         │
    └────────┴─────────┘
         │
    ┌────▼────┐
    │  MySQL  │
    │  Redis  │
    │  OSS    │
    └─────────┘
```

### 微服务模块说明

| 模块 | 端口 | 说明 |
|------|------|------|
| **VisionWear-GateWay** | 8080 | API网关，统一入口，路由转发，认证拦截 |
| **VisionWear-User** | 8081 | 用户服务，负责用户注册、登录、个人信息管理 |
| **VisionWear-Image** | 8082 | 图像服务，负责AI图像生成、处理、存储 |
| **VisionWear-Community** | 8083 | 社区服务，负责帖子、点赞、收藏、评论等 |
| **VisionWear-Common** | - | 公共模块，提供通用工具类、配置、异常处理 |
| **VisionWear-Api** | - | API模块，定义Feign客户端接口 |

---

## 🛠️ 技术栈

### 后端技术栈

#### 核心框架
- **Java 17** - 编程语言
- **Spring Boot 3.2.2** - 应用框架
- **Spring Cloud 2023.0.1** - 微服务框架
- **Spring Cloud Alibaba 2023.0.1.0** - 微服务组件

#### 数据存储
- **MySQL 8.3.0** - 关系型数据库
- **MyBatis-Plus 3.5.5** - ORM框架
- **Redis** - 缓存数据库
- **Caffeine 3.1.8** - 本地缓存

#### 认证与安全
- **JWT (jjwt 0.12.6)** - 无状态认证
- **Spring Security** - 安全框架

#### 文档与工具
- **Knife4j 4.4.0** - API文档工具
- **Swagger/OpenAPI** - API规范
- **Lombok 1.18.30** - 代码简化
- **Hutool 5.8.22** - Java工具库

#### 云服务集成
- **阿里云OSS 3.10.2** - 对象存储服务
- **阿里云百炼 (DashScope) 2.20.6** - AI图像生成
- **腾讯云AI 3.1.1223** - AI图像生成
- **火山引擎SDK 1.0.225** - AI图像生成

#### 其他
- **OkHttp 4.12.0** - HTTP客户端
- **FastJSON 1.2.62** - JSON处理
- **Commons IO 2.11.0** - IO工具

### 前端技术栈

#### 核心框架
- **Vue 3.5.13** - 渐进式JavaScript框架
- **Vite 6.2.0** - 下一代前端构建工具
- **Vue Router 4.5.0** - 路由管理

#### UI组件库
- **Element Plus 2.9.7** - Vue 3组件库
- **@element-plus/icons-vue 2.3.1** - 图标库
- **@arco-design/web-vue 2.57.0** - 备用UI组件库

#### 状态管理
- **Pinia 3.0.2** - 状态管理库

#### 网络请求
- **Axios 1.8.4** - HTTP客户端

---

## 🎯 核心功能

### 1. AI图像生成模块

#### 📝 文本生成图像 (Text-to-Image)
- 基于文本描述生成高质量时尚图像
- 支持多种风格预设和参数调节
- 集成多个AI模型，提供多样化生成效果

#### 🎨 风格延伸 (Style Extension)
- 将现有图片转换为不同艺术风格
- 支持多种风格模板选择
- 保持原图内容的同时改变风格

#### ✏️ 线稿成图 (Sketch-to-Image)
- 将手绘线稿快速转化为完整图像
- 智能识别线稿内容并填充细节
- 支持多种渲染风格

#### 🖌️ 局部重绘 (Partial Redraw)
- 针对图像特定区域进行重新绘制
- 精确控制重绘区域和内容
- 保持整体图像一致性

#### 🖼️ 图像融合 (Image Fusion)
- 多图像智能融合
- 风格迁移和内容合成

### 2. 用户管理模块

- **用户注册/登录**：支持邮箱、手机号注册，JWT认证
- **个人信息管理**：头像、昵称、个人简介等
- **我的作品**：查看和管理自己生成的所有图像
- **微信登录**：支持微信第三方登录（待完善）

### 3. 社区模块

- **帖子发布**：支持图文、纯文字、图片分享等多种类型
- **帖子管理**：编辑、删除、置顶等操作
- **互动功能**：点赞、收藏、评论、分享
- **标签系统**：支持添加标签，便于分类和搜索
- **热门推荐**：基于浏览量和互动数据推荐热门内容

### 4. 素材管理模块

- **素材库**：管理和使用设计素材
- **素材上传**：支持多种格式的素材上传

---

## 📁 项目结构

```
web-qvva-WtuCode/
├── backend/                          # 后端微服务项目
│   ├── VisionWear-GateWay/          # API网关服务
│   │   ├── src/main/java/com/wtu/
│   │   │   ├── config/              # 网关配置（CORS等）
│   │   │   ├── controller/          # Swagger资源控制器
│   │   │   ├── filters/             # 认证过滤器
│   │   │   └── properties/          # JWT配置属性
│   │   └── src/main/resources/
│   │       ├── application.yml       # 应用配置
│   │       └── bootstrap.yml        # 启动配置
│   │
│   ├── VisionWear-User/             # 用户服务
│   │   ├── src/main/java/com/wtu/
│   │   │   ├── controller/          # 用户控制器
│   │   │   ├── service/             # 用户业务逻辑
│   │   │   ├── mapper/              # MyBatis映射
│   │   │   ├── entity/              # 用户实体
│   │   │   ├── dto/                 # 数据传输对象
│   │   │   └── vo/                  # 视图对象
│   │   └── src/main/resources/
│   │
│   ├── VisionWear-Image/            # 图像服务
│   │   ├── src/main/java/com/wtu/
│   │   │   ├── controller/          # 图像控制器
│   │   │   ├── service/             # 图像业务逻辑（AI生成）
│   │   │   ├── mapper/              # 图像数据访问
│   │   │   ├── entity/              # 图像实体
│   │   │   ├── dto/                 # 请求DTO
│   │   │   └── vo/                  # 响应VO
│   │   └── src/main/resources/
│   │
│   ├── VisionWear-Community/        # 社区服务
│   │   ├── src/main/java/com/wtu/
│   │   │   ├── controller/          # 帖子控制器
│   │   │   ├── service/             # 帖子业务逻辑
│   │   │   ├── mapper/              # 帖子数据访问
│   │   │   ├── entity/              # 帖子、标签等实体
│   │   │   └── dto/                 # 帖子DTO
│   │   └── src/main/resources/
│   │
│   ├── VisionWear-Common/            # 公共模块
│   │   ├── src/main/java/com/wtu/
│   │   │   ├── config/              # 公共配置（Redis、OSS等）
│   │   │   ├── entity/              # 公共实体
│   │   │   ├── exception/           # 异常定义
│   │   │   ├── handler/             # 全局异常处理
│   │   │   ├── result/              # 统一响应结果
│   │   │   ├── utils/               # 工具类（JWT、OSS、Redis等）
│   │   │   └── properties/          # 配置属性类
│   │   └── src/main/resources/
│   │
│   ├── VisionWear-Api/              # API模块
│   │   └── src/main/java/com/wtu/
│   │       └── client/              # Feign客户端接口
│   │
│   └── pom.xml                      # Maven父POM
│
├── frontend/                         # 前端项目（Vue 3）
│   ├── src/
│   │   ├── api/                     # API接口定义
│   │   │   ├── modules/             # 按模块划分的API
│   │   │   │   ├── auth.js         # 认证相关API
│   │   │   │   ├── user.js         # 用户相关API
│   │   │   │   ├── image.js        # 图像相关API
│   │   │   │   └── material.js     # 素材相关API
│   │   │   └── request.js          # Axios请求封装
│   │   │
│   │   ├── views/                   # 页面视图
│   │   │   ├── auth/               # 认证页面（登录、注册）
│   │   │   ├── fashion/            # 时尚设计页面
│   │   │   ├── image-processing/   # 图像处理页面
│   │   │   ├── design/             # 设计相关页面
│   │   │   └── user/               # 用户中心页面
│   │   │
│   │   ├── components/              # 可复用组件
│   │   │   └── rawingCanvas.vue    # 画布组件
│   │   │
│   │   ├── router/                  # 路由配置
│   │   ├── store/                   # Pinia状态管理
│   │   │   └── modules/            # 按模块划分的store
│   │   ├── services/                # 业务服务层
│   │   ├── utils/                   # 工具函数
│   │   └── styles/                  # 样式文件
│   │
│   ├── public/                       # 公共静态资源
│   ├── index.html                    # HTML模板
│   ├── vite.config.js                # Vite配置
│   └── package.json                  # 依赖配置
│
├── refrontend/                       # 前端重构版本（可选）
│   └── ...                          # 类似frontend结构
│
├── images/                           # 项目图片资源
├── deploy.sh                         # 部署脚本
└── README.md                         # 项目说明文档
```

---

## 🔧 环境要求

### 开发环境

- **JDK**: 17+
- **Node.js**: 16+
- **Maven**: 3.6+
- **MySQL**: 8.0+
- **Redis**: 5.0+（可选，用于缓存）

### 云服务配置

- **阿里云OSS**：用于图像存储
- **AI服务**：需要配置以下至少一种AI服务的API密钥
  - 阿里云百炼（DashScope）
  - 腾讯云AI
  - 火山引擎

---

## 🚀 快速开始

### 1. 克隆项目

```bash
git clone <repository-url>
cd web-qvva-WtuCode
```

### 2. 数据库配置

创建MySQL数据库，并执行SQL脚本初始化表结构。

### 3. 后端配置

#### 3.1 修改配置文件

编辑各服务的 `application-dev.yml` 文件，配置数据库连接、Redis、OSS等信息：

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/visionwear?useUnicode=true&characterEncoding=utf8&serverTimezone=Asia/Shanghai
    username: your_username
    password: your_password
  
  data:
    redis:
      host: localhost
      port: 6379
      password: your_redis_password
```

#### 3.2 配置云服务

在各服务的配置文件中添加云服务配置：

```yaml
ali:
  oss:
    endpoint: your_oss_endpoint
    access-key-id: your_access_key_id
    access-key-secret: your_access_key_secret
    bucket-name: your_bucket_name
```

#### 3.3 启动后端服务

按以下顺序启动服务：

```bash
# 1. 启动网关服务
cd backend/VisionWear-GateWay
mvn spring-boot:run

# 2. 启动用户服务
cd ../VisionWear-User
mvn spring-boot:run

# 3. 启动图像服务
cd ../VisionWear-Image
mvn spring-boot:run

# 4. 启动社区服务
cd ../VisionWear-Community
mvn spring-boot:run
```

或者使用IDE（如IntelliJ IDEA）直接运行各服务的 `Application.java` 主类。

### 4. 前端配置

#### 4.1 安装依赖

```bash
cd frontend
npm install
```

#### 4.2 配置API地址

编辑 `src/api/request.js`，配置后端API地址：

```javascript
const baseURL = 'http://localhost:8080/api'  // 网关地址
```

#### 4.3 启动前端

```bash
npm run dev
```

前端服务将在 `http://localhost:5173` 启动（Vite默认端口）。

### 5. 访问应用

- **前端地址**: http://localhost:5173
- **API文档**: http://localhost:8080/doc.html (Knife4j)
- **网关地址**: http://localhost:8080

---

## 📦 部署指南

### 生产环境部署

#### 1. 修改配置

**前端配置**：
编辑 `frontend/src/api/request.js`，将 `baseURL` 修改为生产环境地址：

```javascript
const baseURL = 'http://8.155.5.178:8080/api'  // 生产环境网关地址
```

**后端配置**：
修改各服务的 `application.yml` 或 `application-prod.yml`，配置生产环境数据库、Redis等。

#### 2. 使用部署脚本

项目提供了自动化部署脚本 `deploy.sh`：

```bash
chmod +x deploy.sh
./deploy.sh
```

脚本将执行以下操作：
1. 编译后端项目（Maven打包）
2. 上传后端JAR包到服务器
3. 编译前端项目（npm build）
4. 上传前端dist目录到服务器

#### 3. 手动部署

**后端部署**：
```bash
cd backend
mvn clean package -DskipTests
# 将生成的JAR包上传到服务器并运行
java -jar VisionWear-User/target/VisionWear-User-0.0.1-SNAPSHOT.jar
```

**前端部署**：
```bash
cd frontend
npm run build
# 将dist目录上传到Nginx等Web服务器
```

#### 4. 服务器配置

建议使用Nginx作为反向代理和静态资源服务器：

```nginx
server {
    listen 80;
    server_name your_domain.com;

    # 前端静态资源
    location / {
        root /opt/vision-wear/dist;
        try_files $uri $uri/ /index.html;
    }

    # 后端API代理
    location /api {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

---

## 📚 API文档

项目集成了Knife4j（Swagger增强版），启动后端服务后可通过以下地址访问API文档：

- **开发环境**: http://localhost:8080/doc.html
- **生产环境**: http://your-domain.com/doc.html

API文档包含：
- 所有接口的详细说明
- 请求参数和响应示例
- 在线测试功能
- 接口分组和搜索

---

## 🔐 认证说明

项目采用JWT（JSON Web Token）进行无状态认证：

1. **登录流程**：用户登录后，后端返回JWT Token
2. **Token存储**：前端将Token存储在LocalStorage或SessionStorage
3. **请求携带**：每次API请求在Header中携带Token：`Authorization: Bearer <token>`
4. **网关验证**：Gateway统一验证Token，解析用户信息并传递给下游服务

---

## 🗄️ 数据库设计

### 核心表结构

- **user**: 用户表
- **image**: 图像表
- **post**: 帖子表
- **post_image**: 帖子图片关联表
- **post_tag**: 帖子标签关联表
- **tag**: 标签表
- **material**: 素材表

详细表结构请参考各服务模块的Entity类或数据库设计文档。

---

## 🧪 开发规范

### 代码规范

- **Java**: 遵循阿里巴巴Java开发手册
- **Vue**: 遵循Vue 3官方风格指南
- **命名规范**: 
  - Java: 驼峰命名（类名大驼峰，方法/变量小驼峰）
  - Vue: 组件名大驼峰，变量/方法小驼峰

### Git提交规范

建议使用Conventional Commits规范：

```
feat: 新功能
fix: 修复bug
docs: 文档更新
style: 代码格式调整
refactor: 代码重构
test: 测试相关
chore: 构建/工具相关
```

---

## 🐛 常见问题

### 1. 后端服务启动失败

- 检查JDK版本是否为17+
- 检查MySQL和Redis是否启动
- 检查配置文件中的数据库连接信息

### 2. 前端无法连接后端

- 检查 `src/api/request.js` 中的 `baseURL` 配置
- 检查后端服务是否正常启动
- 检查CORS配置是否正确

### 3. 图像生成失败

- 检查AI服务的API密钥配置
- 检查网络连接
- 查看后端日志获取详细错误信息

### 4. OSS上传失败

- 检查阿里云OSS配置是否正确
- 检查Bucket权限设置
- 检查网络连接

---

## 📝 更新日志

### v0.0.1 (当前版本)

- ✅ 完成用户注册、登录功能
- ✅ 完成AI图像生成核心功能（文生图、风格延伸、线稿成图、局部重绘）
- ✅ 完成社区帖子功能（发布、查看、编辑、删除）
- ✅ 完成图像存储和管理
- ✅ 完成微服务架构搭建
- ✅ 完成API文档集成

---

## 🤝 贡献指南

欢迎提交Issue和Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

---

## 🙏 致谢

- [Spring Boot](https://spring.io/projects/spring-boot)
- [Vue.js](https://vuejs.org/)
- [Element Plus](https://element-plus.org/)
- [MyBatis-Plus](https://baomidou.com/)
- 以及所有使用的开源库和工具

---

<div align="center">

**如果这个项目对你有帮助，请给一个 ⭐ Star！**

Made with ❤️ by WTU Team

</div>
