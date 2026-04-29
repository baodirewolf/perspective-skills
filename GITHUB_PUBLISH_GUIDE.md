# GitHub 发布指南

## 🚀 快速导入到GitHub

### 方法一：使用 GitHub CLI (推荐)

如果你本地安装了 `gh` 命令行工具：

```bash
# 1. 登录GitHub
gh auth login

# 2. 克隆仓库
gh repo clone baodirewolf/perspective-skills
cd perspective-skills

# 3. 复制文件（从服务器下载后解压到这里）
# 将 perspective-skills-v1.0.0.tar.gz 解压到当前目录

# 4. 提交并推送
git add .
git commit -m "Release v1.0.0: 4 perspective skills

- 倪海厦：中医经方、紫微斗数、八字命理、五术合一
- 南怀瑾：儒释道三教合一、经史合参、国学智慧
- 荣格：集体无意识、原型、梦境分析、个体化
- 阿德勒：目的论、自卑与超越、课题分离、社会兴趣

基于女娲Skill方法论 v2.0 蒸馏"

git push origin main
```

---

### 方法二：使用 Git 命令行

```bash
# 1. 配置Git（如果还没配置）
git config --global user.name "baodirewolf"
git config --global user.email "你的邮箱@example.com"

# 2. 克隆空仓库
git clone https://github.com/baodirewolf/perspective-skills.git
cd perspective-skills

# 3. 复制所有文件到该目录
# cp -r /path/to/downloaded/perspective-skills/* ./

# 4. 提交并推送
git add .
git commit -m "Release v1.0.0: 4 perspective skills"
git push origin main
```

---

### 方法三：GitHub 网页上传（最简单）

1. 访问 https://github.com/baodirewolf/perspective-skills
2. 点击 **"uploading an existing file"** 链接
3. 拖拽或选择以下文件上传：
   - `README.md`
   - `LICENSE`
   - `.gitignore`
   - `ni-haixia-perspective/SKILL.md`
   - `nanhuaijin-perspective/SKILL.md`
   - `jung-perspective/SKILL.md`
   - `adler-perspective/SKILL.md`
4. 填写提交信息：
   - Commit message: `Release v1.0.0: 4 perspective skills`
   - Description: 添加上述4个人物技能
5. 点击 **"Commit changes"**

---

### 方法四：GitHub Desktop

1. 下载并安装 [GitHub Desktop](https://desktop.github.com/)
2. 登录你的GitHub账号
3. 点击 **File** → **Clone repository**
4. 选择 `baodirewolf/perspective-skills`
5. 点击 **Clone**
6. 将下载的文件复制到本地仓库目录
7. 在GitHub Desktop中填写提交信息
8. 点击 **Commit to main** → **Push origin**

---

## 📦 文件清单

上传时需要包含以下文件：

```
perspective-skills/
├── README.md          # 项目说明
├── LICENSE            # MIT许可证
├── .gitignore         # Git忽略配置
├── .github/
│   └── workflows/
│       └── auto-push.yml  # GitHub Actions配置
├── ni-haixia-perspective/
│   └── SKILL.md       # 倪海厦技能
├── nanhuaijin-perspective/
│   └── SKILL.md       # 南怀瑾技能
├── jung-perspective/
│   └── SKILL.md       # 荣格技能
└── adler-perspective/
    └── SKILL.md       # 阿德勒技能
```

---

## ✅ 验证发布成功

推送完成后，访问：
https://github.com/baodirewolf/perspective-skills

你应该能看到：
- ✅ README.md 内容正确显示
- ✅ 4个Skill文件夹
- ✅ LICENSE文件
- ✅ 绿色 ✅ 标记（表示CI通过，如果配置了Actions）

---

## 🏷️ 创建 Release（可选）

发布后可以创建GitHub Release：

1. 访问 https://github.com/baodirewolf/perspective-skills/releases
2. 点击 **"Create a new release"**
3. 选择标签：**v1.0.0**（或点击"Create new tag"）
4. 填写发布标题：**Perspective Skills v1.0.0**
5. 填写发布说明（参考下方模板）
6. 点击 **"Publish release"**

### Release 模板

```markdown
## Perspective Skills v1.0.0

基于 [Nuwa Skill 造人术](https://github.com/openclaw/openclaw/tree/main/skills/nuwa-skill) 蒸馏的4个人物思维视角。

### 包含技能

| 技能 | 核心能力 |
|------|---------|
| 倪海厦 | 中医经方、紫微斗数、八字命理、五术合一 |
| 南怀瑾 | 儒释道三教合一、经史合参、国学智慧 |
| 荣格 | 集体无意识、原型、梦境分析、个体化 |
| 阿德勒 | 目的论、自卑与超越、课题分离、社会兴趣 |

### 快速安装

```bash
clawhub install ni-haixia-perspective
clawhub install nanhuaijin-perspective
clawhub install jung-perspective
clawhub install adler-perspective
```

### 使用方法

说出触发词即可激活对应人物视角：
- 倪海厦：「倪海夏」「中医」「紫微斗数」「八字命理」「玄学」
- 南怀瑾：「南怀瑾」「国学」「儒释道」「三教合一」「禅修」
- 荣格：「荣格」「Jung」「心理学」「梦境」「原型」「集体无意识」
- 阿德勒：「阿德勒」「Adler」「目的论」「课题分离」「自卑与超越」
```

---

## 🆘 遇到问题？

### 问题1：权限错误
```
fatal: unable to access 'https://github.com/...': The requested URL returned error: 403
```
**解决**：检查token权限，或改用SSH方式：
```bash
git remote set-url origin git@github.com:baodirewolf/perspective-skills.git
```

### 问题2：文件太大
```
remote: error: File is too large
```
**解决**：research目录下的文件可能很大，可以不上传：
```bash
echo "references/sources/" >> .gitignore
echo "references/research/" >> .gitignore
git add .gitignore
git commit -m "Ignore large research files"
```

### 问题3：冲突
```
error: failed to push some refs to 'https://github.com/...'
```
**解决**：先拉取再推送：
```bash
git pull origin main --rebase
git push origin main
```

---

## 📞 需要帮助？

如果遇到问题，可以：
1. 检查GitHub仓库状态：https://github.com/baodirewolf/perspective-skills
2. 查看GitHub文档：https://docs.github.com
3. 联系支持：将错误信息复制给AI助手

---

**祝你发布顺利！** 🎉