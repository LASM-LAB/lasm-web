# LASM 网站内容编辑手册

本文档说明如何通过编辑 `public/lasm-web/content/` 目录下的 Markdown 文件来更新网站内容。所有内容均采用 Markdown + YAML Frontmatter 格式存储，无需数据库。

---

## 目录结构

```
public/lasm-web/content/
├── home/home.md                    # 首页配置
├── people/
│   └── people.md                   # 团队成员
├── research/
│   └── research.md                 # 研究方向与项目
├── publications/
│   └── publications.md             # 发表论文
├── news/
│   ├── 2024-12-15-xxx.md           # 新闻文章
│   ├── images/
│   │   └── xxx.png                 # 新闻配图
│   └── videos/
│       └── demo.mp4                # 新闻视频
├── contact/
│   └── contact.md                  # 联系方式与招生
└── ...
```

> **重要约定**：每个目录下的 `images/` 子目录存放该板块的图片，在 Markdown 中引用时使用相对路径 `images/xxx.png`。

---

## 一、首页配置 (`home/home.md`)

```yaml
---
heroImage: images/banner.jpg          # 首页 Hero 区域大图
logo: images/lab-logo.png              # 实验室 Logo（可选，不指定则使用默认图标）
heroTitle: LASM 实验室                  # 主标题
heroSubtitle: Learning Algorithm and Soft Manipulation Laboratory
heroChineseSubtitle: 学习算法与软体操作实验室
heroDescription: 致力于机器人学、具身智能和灵巧手操作等前沿方向的研究，推动智能机器人技术的发展与应用。
labName: 武汉大学机器人学院            # 副标题/学院名称
ctaPrimary: 研究方向                   # 主按钮文字
ctaPrimaryHref: /research              # 主按钮链接
ctaSecondary: 加入我们                # 次按钮文字
ctaSecondaryHref: /contact             # 次按钮链接
---
```

### 字段说明

| 字段 | 必填 | 说明 |
|------|------|------|
| `heroImage` | 否 | 首页顶部大图，建议使用 `images/文件名.jpg` 相对路径 |
| `logo` | 否 | 实验室 Logo，显示在导航栏和页脚。不填则使用默认图标 |
| `heroTitle` | 是 | 首页主标题 |
| `heroSubtitle` | 是 | 英文副标题 |
| `heroChineseSubtitle` | 是 | 中文副标题 |
| `heroDescription` | 是 | 实验室简介 |
| `labName` | 是 | 学院名称，显示在 Logo 下方 |

---

## 二、团队成员 (`people/people.md`)

```yaml
---
list:
  - name: 张教授
    title: 实验室主任 / 教授 / 博士生导师
    department: 武汉大学机器人学院
    research: 机器人学、具身智能、灵巧操作
    email: zhang.prof@whu.edu.cn
    type: faculty
    avatar: images/avatar-zhang.jpg
    order: 1

  - name: 陈同学
    year: 2022级博士
    research: 灵巧手抓取规划
    type: phd
    avatar: images/avatar-chen.jpg
    order: 5

  - name: 马校友
    period: 2021-2024
    current: 现就职于华为技术有限公司
    type: alumni
    avatar: ''
    order: 13
---
```

### 人员类型 (`type`)

| 类型值 | 说明 | 适用字段 |
|--------|------|----------|
| `faculty` | 指导教师（教授、副教授） | `name`, `title`, `department`, `research`, `email`, `type`, `avatar`, `order` |
| `postdoc` | 博士后 | 同 `faculty` |
| `phd` | 博士研究生 | `name`, `year`, `research`, `type`, `avatar`, `order` |
| `master` | 硕士研究生 | `name`, `year`, `research`, `type`, `avatar`, `order` |
| `undergrad` | 本科生与实习生 | `name`, `year`, `research`, `type`, `avatar`, `order` |
| `engineer` | 科研助理 / 工程师 | `name`, `title`, `research`, `type`, `avatar`, `order` |
| `robot` | 机器人 | `name`, `title`, `research`, `type`, `avatar`, `order` |
| `alumni` | 已毕业校友 | `name`, `period`, `current`, `type`, `avatar`, `order` |

### 字段说明

| 字段 | 说明 |
|------|------|
| `name` | 姓名 |
| `type` | 人员类型（见上表） |
| `avatar` | 头像图片路径，如 `images/xxx.png`。不填则显示姓名首字母 |
| `order` | 排序序号，数值越小越靠前 |
| `title` | 职称（仅 faculty/postdoc） |
| `department` | 所属学院（仅 faculty/postdoc） |
| `email` | 邮箱（仅 faculty/postdoc） |
| `year` | 入学年级（仅 phd/master） |
| `research` | 研究方向 |
| `period` | 就读期间（仅 alumni） |
| `current` | 毕业去向（仅 alumni） |

> **头像建议**：上传竖版人像照片（3:4 比例），人物主体在上半身。系统会自动缩放图像以完整适配展示框，不会裁剪。如果图像尺寸过大，上传时会自动压缩优化。

---

## 三、研究方向与项目 (`research/research.md`)

### 研究方向 (`areas`)

```yaml
---
areas:
  - id: "robotics"
    title: "机器人学"
    subtitle: "Robotics"
    icon: "Bot"
    description: "研究机器人系统的设计、建模、控制与优化..."
    topics:
      - "移动机器人自主导航"
      - "协作机器人安全交互"
      - "仿人机器人运动控制"
      - "机器人系统设计与集成"

  - id: "embodied"
    title: "具身智能"
    subtitle: "Embodied Intelligence"
    icon: "Brain"
    description: "探索物理世界中的人工智能..."
    topics:
      - "视觉-语言-动作模型"
      - "开放环境任务规划"
---
```

### 研究项目 (`projects`)

```yaml
projects:
  - title: "软体灵巧手自适应抓取系统"
    area: "灵巧手操作 / 软体机器人"
    description: "开发具有柔性手指的仿人灵巧手系统..."
    status: "进行中"
    fundedBy: "国家自然科学基金"
```

### 可选图标 (`icon`)

使用 [Lucide Icons](https://lucide.dev/icons/) 图标名称：`Bot`, `Brain`, `Hand`, `Eye`, `CircuitBoard`, `Cpu`, `Globe`, `Layers`, `Zap`, `Database` 等。

---

## 四、发表论文 (`publications/publications.md`)

```yaml
---
list:
  - title: 'SoftGrip: A Soft Robotic Gripper with Tactile Sensing'
    authors: 'Zhang, S., Li, W., Wang, H., et al.'
    venue: IEEE Transactions on Robotics (T-RO)
    year: 2024
    type: 期刊
    tags:
      - 软体机器人
      - 触觉感知
      - 抓取
    links: "[PDF](https://arxiv.org/pdf/2401.12345.pdf)"

  - title: 'EmbodiedGPT: Vision-Language Pre-training'
    authors: 'Chen, L., Liu, Y., Zhang, S., et al.'
    venue: Conference on Robot Learning (CoRL)
    year: 2024
    type: 会议
    tags:
      - 具身智能
      - 大模型
    links: |
      [PDF](https://arxiv.org/pdf/2402.67890.pdf)
      [CODE](https://github.com/example/softgrip)
      [WEBSITE](https://example.com/project)
---
```

### `links` 字段格式

使用 Markdown 链接语法，每行一个：

```yaml
links: "[PDF](https://arxiv.org/pdf/xxx.pdf)"

# 多链接（用 | 表示多行字符串）
links: |
  [PDF](https://arxiv.org/pdf/xxx.pdf)
  [CODE](https://github.com/xxx)
  [WEBSITE](https://example.com)
```

系统会自动将 `[PDF]`、`[CODE]`、`[WEBSITE]` 渲染为彩色标签按钮。

### 字段说明

| 字段 | 说明 |
|------|------|
| `title` | 论文标题 |
| `authors` | 作者列表 |
| `venue` | 发表期刊/会议 |
| `year` | 发表年份 |
| `type` | `期刊` 或 `会议` |
| `tags` | 关键词标签列表 |
| `links` | 相关链接（PDF、代码、项目页） |

---

## 五、新闻动态 (`news/YYYY-MM-DD-标题.md`)

每个新闻是一个独立的 Markdown 文件，文件名格式：

```
YYYY-MM-DD-新闻标题.md
```

示例：

```markdown
---
date: '2024-12-15'
category: 学术成果
title: 实验室论文被 RSS 2025 接收
summary: 关于软体灵巧手自适应抓取的研究工作被机器人顶级会议 RSS 2025 接收。
image: images/news-cover.jpg
---

实验室关于软体灵巧手自适应抓取的研究工作被机器人学顶级会议 Robotics: Science and Systems (RSS) 2025 接收。该工作提出了一种结合触觉感知与深度强化学习的新型抓取策略，显著提升了机器人在非结构化环境下的操作能力。

![实验示意图](images/figure1.png)

上图展示了我们的方法在不同物体上的抓取效果。
```

### 字段说明

| 字段 | 必填 | 说明 |
|------|------|------|
| `date` | 是 | 发布日期，格式 `YYYY-MM-DD` |
| `category` | 是 | 分类：`学术成果`、`项目资助`、`学术活动`、`团队建设`、`合作交流` |
| `title` | 是 | 新闻标题 |
| `summary` | 是 | 摘要，显示在新闻列表页 |
| `image` | 否 | 封面图路径，如 `images/xxx.png`。不填则无封面 |

### 正文图片与视频

在正文中使用 Markdown 图片语法插入图片：

```markdown
![图片描述](images/photo1.png)
```

> 图片存放于 `public/lasm-web/content/news/images/` 目录下。

#### 视频

新闻正文也支持视频播放，使用与图片相同的 Markdown 语法，视频文件放在 `videos/` 目录下：

```markdown
![视频描述](videos/demo.mp4)
```

> 视频存放于 `public/lasm-web/content/news/videos/` 目录下。
> 支持的格式：`.mp4`、`.webm`、`.mov`、`.ogv`

### 分类标签颜色

| 分类 | 颜色 |
|------|------|
| 学术成果 | 蓝色 |
| 项目资助 | 绿色 |
| 学术活动 | 紫色 |
| 团队建设 | 橙色 |
| 合作交流 | 粉色 |

---

## 六、联系方式 (`contact/contact.md`)

```yaml
---
address: "湖北省武汉市武昌区八一路 299 号"
building: "武汉大学机器人学院"
zipcode: "430072"
email: ""
email2: "zhang.prof@whu.edu.cn"
phone: ""
mobile: "+86-138-xxxx-xxxx"

positions:
  - title: "博士后研究员"
    requirements:
      - "已获得或即将获得机器人学、计算机科学、人工智能等相关专业博士学位"
      - "在机器人学、计算机视觉或机器学习领域有高水平论文发表"
    benefits:
      - "年薪 30-50 万元（税前）"
      - "提供科研启动经费"

  - title: "博士研究生"
    requirements:
      - "具有机器人、自动化、计算机等相关专业背景"
    benefits:
      - "提供具有竞争力的助研津贴"
      - "支持参加国内外学术会议"
---
```

### 字段说明

| 字段 | 说明 |
|------|------|
| `address` | 地址 |
| `building` | 所在建筑/学院 |
| `zipcode` | 邮编 |
| `email` | 实验室邮箱 |
| `email2` | 备用邮箱 |
| `phone` | 固定电话 |
| `mobile` | 手机 |
| `positions` | 招生职位列表，每个职位包含 `title`、`requirements`、`benefits` |

---

## 图像路径约定

### 路径格式

所有图片引用均使用**相对当前 MD 文件所在目录**的路径：

```yaml
# home/home.md 中
heroImage: images/banner.jpg
logo: images/logo.png

# people/people.md 中
avatar: images/avatar-zhang.jpg

# news/2024-12-15-xxx.md 中
image: images/cover.jpg
```

### 实际存储位置

| MD 文件位置 | 媒体存放位置 | 浏览器访问路径 |
|-------------|-------------|---------------|
| `public/lasm-web/content/home/home.md` | `public/lasm-web/content/home/images/` | `/lasm-web/content/home/images/xxx.png` |
| `public/lasm-web/content/people/people.md` | `public/lasm-web/content/people/images/` | `/lasm-web/content/people/images/xxx.png` |
| `public/lasm-web/content/news/xxx.md` | `public/lasm-web/content/news/images/` | `/lasm-web/content/news/images/xxx.png` |
| `public/lasm-web/content/news/xxx.md` | `public/lasm-web/content/news/videos/` | `/lasm-web/content/news/videos/xxx.mp4` |

### 图片上传方式

**方式一：通过 Admin 后台**

1. 访问 `/admin` 进入内容管理后台
2. 选择对应板块（首页配置、团队成员、新闻动态等）
3. 在图片字段点击「选择文件」或「粘贴图片」上传
4. 系统自动保存图片并填入路径

**方式二：手动放置**

1. 将图片文件放入对应目录的 `images/` 文件夹
2. 在 MD 文件中手动填写路径 `images/文件名.png`

### 推荐图片规格

| 用途 | 推荐尺寸 | 格式 |
|------|----------|------|
| Logo | 200x200 ~ 500x500 | PNG (透明背景) |
| 首页 Hero 大图 | 1920x1080 | JPG |
| 人物头像 | 3:4 竖版 (600x800) | JPG/PNG |
| 新闻封面 | 16:9 横版 (800x450) | JPG |
| 新闻正文配图 | 宽度 800px 以上 | JPG/PNG |

---

## 编辑后生效

修改 MD 文件后，**刷新浏览器页面**即可看到更新，无需重新构建或重启服务。

---

## 常见问题

**Q: 图片不显示？**
A: 检查图片是否放在正确的 `images/` 目录下，路径是否为 `images/xxx.png` 格式。

**Q: 新增新闻如何操作？**
A: 在 `public/lasm-web/content/news/` 下新建文件，文件名格式为 `YYYY-MM-DD-标题.md`。

**Q: 如何删除一条新闻？**
A: 直接删除对应的 `.md` 文件即可。

**Q: 修改后页面没变化？**
A: 按 Ctrl+F5 强制刷新浏览器缓存。

**Q: 排序怎么调整？**
A: 在 `people/people.md` 中调整 `order` 字段数值（越小越靠前）。新闻按日期自动排序。
