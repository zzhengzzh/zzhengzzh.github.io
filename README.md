# 赵志恒的个人主页

正式网站：**https://zzhengzzh.github.io/**  
英文页面：https://zzhengzzh.github.io/en.html

这是一个使用 HTML 和 CSS 编写的中英文静态个人主页。修改 `main` 分支中的文件后，GitHub Pages 自动部署更新。维护不需要安装网页框架，也不需要运行生成脚本。

## 1. 找到要修改的文件

| 修改内容 | 文件 |
| --- | --- |
| 中文介绍、项目、奖项、教育及校园经历 | [index.html](index.html) |
| 对应的英文内容 | [en.html](en.html) |
| 字号、颜色、间距、手机布局 | [styles.css](styles.css) |
| 头像 | [images/profile.jpg](images/profile.jpg) |
| 维护说明 | [README.md](README.md) |

**中文和英文目前分别维护。修改中文后，也要修改英文对应位置。** `README.md` 是仓库说明，网站正文来自 `index.html` 和 `en.html`。

## 2. 最简单的方法：直接在 GitHub 网页修改

1. 登录 GitHub，打开本仓库，确认当前分支为 `main`。
2. 点击目标文件，再点右上角的铅笔图标（Edit this file）。
3. 在编辑框中找到内容；可以使用 `Ctrl + F` 搜索文字或本说明中的定位标记。文件中有些 HTML 行较长，按文字搜索比按行号查找更方便。
4. 修改后点 **Commit changes**，填写说明，例如“更新研究方向”。选择提交到 `main` 并确认。
5. 修改另一种语言的对应文件；需要一次修改多个文件时，可在仓库页面按英文句号键 `.` 打开 github.dev 编辑器，编辑后在 Source Control 中提交到 `main`。
6. 打开 [Actions](https://github.com/zzhengzzh/zzhengzzh.github.io/actions)，查看最新的 `pages build and deployment`。本次运行显示绿色对勾后，再访问正式网站确认。

GitHub 文件编辑器里的预览不能代替网页实际显示效果。修改布局时，建议使用下面的本地预览方法。

## 3. 修改一句话

例如搜索“目前研究电力电子与人工智能”，找到简介所在的 `<p>...</p>`，只修改标签中间的文字：

```html
<p>这里填写更新后的个人介绍。</p>
```

常用标签：

| 标签 | 用途 |
| --- | --- |
| `<p>文字</p>` | 一段正文 |
| `<h2>文字</h2>` | 大栏目标题 |
| `<h3 class="subheading">文字</h3>` | 分组标题，例如“校园任职” |
| `<h4>文字</h4>` | 分组下的条目标题，例如“团支部书记” |
| `<li>文字</li>` | 列表中的一条内容，放在 `<ul>` 或 `<ol>` 中 |
| `<strong>文字</strong>` | 强调文字 |
| `<a href="https://example.com/">文字</a>` | 外部链接 |

保留成对的开始和结束标签。正文中的 `<` 写成 `&lt;`，`&` 写成 `&amp;`，避免被当成 HTML 语法。保存时使用 UTF-8 编码。

修改研究方向时，检查是否还要同步页面顶部的 `<title>`、`<meta name="description">`、简介和研究方向区块。这里的 `<title>` 控制浏览器标签页标题。

## 4. 新增一个项目

在 `index.html` 搜索 `id="projects"`。该区块的结构是：

```html
<section id="projects">
  <!-- 栏目标题 -->
  <!-- 一个或多个 article，每个 article 是一个完整项目 -->
</section>
```

把下面的整个 `<article>...</article>` 插入这个栏目内，放在其他项目之前或之后，**不要放到 `</section>` 外面**。填写真实项目名称、职责和成果；示例文字需要替换后再提交。

```html
<article class="project">
  <div class="project-top">
    <span class="eyebrow">03 / EMBEDDED SYSTEMS</span>
    <span class="date">2026/03 — 2026/08</span>
  </div>
  <h3>填写项目名称</h3>
  <p class="role">填写本人职责</p>
  <ul>
    <li>项目要解决什么问题。</li>
    <li>本人完成了哪些设计、开发或调试工作。</li>
    <li>已经验证的结果或成果。</li>
  </ul>
  <div class="tags">
    <span>DSP</span>
    <span>FPGA</span>
  </div>
</article>
```

- `03` 是项目序号，根据放置顺序调整；它与大栏目序号分别计数。
- 日期统一用 `YYYY/MM — YYYY/MM`；仍在进行可写 `YYYY/MM — 至今`，英文对应 `YYYY/MM — Present`。
- 技术标签按实际使用情况填写，不需要的标签可以删除。
- 如有公开代码或演示，可在 `</article>` 前加入链接：

```html
<p><a href="https://github.com/你的用户名/项目仓库">查看代码 ↗</a></p>
```

- 如需配图，先把图片放入 `images/`，再在项目内加入：

```html
<img src="images/project-demo.jpg"
     alt="填写图片内容说明"
     style="max-width:100%;height:auto;display:block;">
```

在 `en.html` 的 `id="projects"` 区块内同步增加对应的英文项目，使用同一套 class 和相同图片路径。

## 5. 新增一个大栏目

以新增“论文成果”为例，需要同时增加**导航链接、栏目正文**，并同步英文页。

### 第一步：增加导航

在 `index.html` 搜索 `<nav aria-label="主导航">`，在该 `<nav>` 内合适的位置加入：

```html
<a href="#publications">论文成果</a>
```

### 第二步：增加栏目正文

在 `<main id="main">` 内加入下面的完整区块。例如放在“项目经历”区块之后、“荣誉与证书”区块之前。

```html
<section id="publications">
  <div class="section-heading">
    <span>04</span>
    <h2>论文成果</h2>
  </div>
  <ul>
    <li>
      <strong>填写真实论文标题</strong><br>
      填写作者、期刊或会议名称、年份。
      <a href="https://doi.org/填写真实DOI">论文链接 ↗</a>
    </li>
  </ul>
</section>
```

此处内容是填写示例，实际添加时换成真实信息；没有 DOI 就删除示例链接。接收、预印本和正式发表的状态应准确标注。

### 第三步：检查对应关系和编号

- 导航里的 `href="#publications"` 必须与正文的 `id="publications"` 一致。
- 同一页面的每个 `id` 必须唯一。新增其他栏目时，可以使用 `news`、`activities` 等不同名称。
- 插入后把后续大栏目的序号顺延，例如荣誉改成 `05`、教育改成 `06`、联系改成 `07`。
- 栏目显示顺序由 HTML 区块的排列顺序决定；数字本身不会自动排序。
- 新栏目会继承现有的间距、标题和手机样式，通常无需修改 CSS。

### 第四步：同步英文

在 `en.html` 的 `<nav aria-label="Main navigation">` 内加入：

```html
<a href="#publications">Publications</a>
```

再加入相应英文 `<section id="publications">...</section>`，并同步栏目顺序与序号。页面之间可以使用相同 id，同一页面内不能重复。

## 6. 新增奖励、证书或校园任职

### 新增奖项

搜索“竞赛奖项”或“校园荣誉”，在对应的 `<ul class="awards">` 内加入一条：

```html
<li>
  <span class="date">2026</span>
  <span>填写比赛名称、赛区和奖项等级</span>
</li>
```

按年份倒序放置。年份放在左侧，赛事届次保留在右侧奖项名称里。

### 新增技能证书

搜索“技能证书”，在它后面的 `<ul>` 内加入：

```html
<li>填写证书名称</li>
```

### 新增校园任职

搜索“校园任职”，在现有任职条目之后加入：

```html
<div class="education">
  <span class="date">2025/09 — 2026/07</span>
  <div>
    <h4>填写职务名称</h4>
    <p>填写具体职责和已完成的工作。</p>
  </div>
</div>
```

未知具体日期时，可以使用“本科期间”等准确描述。分组标题用 `h3.subheading`，具体职务用 `h4`，职责用 `p`，保持现有层次。以上修改均需同步英文页面。

## 7. 替换头像、修改配色和字体

**替换头像：**上传新照片到 `images/profile.jpg` 并替换同名文件。若换成 PNG 或其他文件名，需同时修改中英文页面中 `<img class="profile-photo">` 的 `src`。文件名大小写应一致。

**修改配色：**在 `styles.css` 开头的 `:root` 修改变量：

```css
--accent: #0d625b; /* 深青色：链接和强调 */
--wash: #ebf2ef;   /* 浅青色：分组背景 */
--ink: #15373c;    /* 主要文字颜色 */
--muted: #526b6b;  /* 时间和说明文字 */
```

**修改字体层次：**搜索对应选择器，修改其已有规则：

| 选择器 | 控制内容 |
| --- | --- |
| `h1` | 顶部姓名 |
| `h2` | 大栏目标题 |
| `.section-heading>span` | 大栏目序号 |
| `.subheading` | 教育经历、校园任职等分组标题 |
| `.education h4` | 学校、学历和具体职务 |
| `.education p` | 专业、任职说明 |
| `.date` | 日期文字 |

CSS 中的 `@media` 是窄屏样式。修改后同时检查电脑与手机宽度，避免只在一种宽度下合适。

## 8. 在电脑上修改、预览和发布

如果已在本机有这个仓库，直接进入其目录；如果在另一台电脑，先安装 Git 和 Python，再下载仓库：

```powershell
git clone https://github.com/zzhengzzh/zzhengzzh.github.io.git
cd zzhengzzh.github.io
```

开始新一轮维护时，先查看状态、同步远端：

```powershell
git status
git pull --ff-only
```

如果已经有未提交的本地修改，先保留或提交自己的工作再同步。遇到冲突先处理，不使用强制覆盖。

用编辑器打开 HTML/CSS 文件并保存。预览时在仓库目录执行：

```powershell
python -m http.server 8147 --bind 127.0.0.1
```

浏览器访问 http://127.0.0.1:8147/，按 `Ctrl + C` 停止预览服务。预览网址只能在本机使用；分享给别人使用正式网站地址。

确认效果后，在另一个终端提交实际修改的文件。下面以修改中英文页面为例：

```powershell
git diff
git add index.html en.html
git commit -m "Update homepage content"
git push origin main
```

如还修改样式或新增图片，在执行 `git commit` 之前把对应文件加入暂存，例如：

```powershell
git add styles.css images/project-demo.jpg
```

如果首次提交提示需要设置作者身份，在本仓库目录设置后重试（邮箱会随提交记录公开，可使用 GitHub 提供的隐私邮箱）：

```powershell
git config user.name "填写你的名字"
git config user.email "填写你的提交邮箱"
```

保存本地文件只改变本地预览；完成推送、等待 Pages 部署成功后，线上网站才更新。

## 9. 改完检查与常见问题

- 中英文都检查一遍，确认内容和日期对应。
- 点击导航，确认能跳到新增栏目。
- 检查图片、代码链接和邮件链接。
- 示例文字、示例日期与示例链接在发布前替换完整。
- 手机检查文字是否超出屏幕、导航是否遮挡内容。
- 主页没更新：先确认已提交到 `main`，再查最新 Actions 是否成功，最后刷新浏览器或使用无痕窗口。
- 图片不显示：检查是否提交了图片文件、路径是否正确，以及大小写是否一致。
- 修改错了：在 GitHub 文件的 History 中查看旧版本，把需要恢复的内容复制回来，再提交一次；每次修改都有历史可查。

## 10. 用问答方式继续维护

可以在 Codex 中使用 `$personal-homepage`，例如：

> 使用 $personal-homepage，为主页新增一个项目。先问我需要哪些资料，完成中英文版本并给我预览，确认后发布。

也可以直接说明：“修改简介这句话”“新增一项奖励”“增加论文栏目”。继续维护前先同步这个 GitHub 仓库，再修改现有 HTML/CSS 文件，保持双语与栏目层次一致。

## 官方操作参考

- [在 GitHub 上编辑文件](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files)
- [github.dev 网页编辑器](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor)
- [GitHub Pages 发布来源](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
