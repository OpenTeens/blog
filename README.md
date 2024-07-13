# Add blog:
1. install pnpm (`npm install -g pnpm`)
2. install sharp (`pnpm add sharp`)
3. create a new folder in `src/content/posts/` with the name of the blog
4. create a new file named `index.md` in the folder, white your article
5. add the following frontmatter to the file:
```yaml
---
title: .sb3 文件格式
description: Scratch 如何保存 “图形化” 的程序？让我们一起探索 Scratch 的 .sb3 文件格式。
published: 2024-07-12
tags:
    - 黄瓜大帝
    - Scratch
    - TC3
    - 开源知识库
category: "开源知识库"
image: "./cover.jpg"
---
```

# 🍥Fuwari

A static blog template built with [Astro](https://astro.build).

[**🖥️Live Demo (Vercel)**](https://fuwari.vercel.app)&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;[**🌏中文 README**](https://github.com/saicaca/fuwari/blob/main/README.zh-CN.md)&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;[**🌏日本語 README**](https://github.com/saicaca/fuwari/blob/main/README.ja-JP.md)&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;[**📦Old Hexo Version**](https://github.com/saicaca/hexo-theme-vivia)

![Preview Image](https://raw.githubusercontent.com/saicaca/resource/main/fuwari/home.png)

## ✨ Features

- [x] Built with [Astro](https://astro.build) and [Tailwind CSS](https://tailwindcss.com)
- [x] Smooth animations and page transitions
- [x] Light / dark mode
- [x] Customizable theme colors & banner
- [x] Responsive design
- [ ] Comments
- [x] Search
- [ ] TOC

## 🚀 How to Use

1. [Generate a new repository](https://github.com/saicaca/fuwari/generate) from this template or fork this repository.
2. To edit your blog locally, clone your repository, run `pnpm install` AND `pnpm add sharp` to install dependencies.  
   - Install [pnpm](https://pnpm.io) `npm install -g pnpm` if you haven't.
3. Edit the config file `src/config.ts` to customize your blog.
4. Run `pnpm new-post <filename>` to create a new post and edit it in `src/content/posts/`.
5. Deploy your blog to Vercel, Netlify, GitHub Pages, etc. following [the guides](https://docs.astro.build/en/guides/deploy/). You need to edit the site configuration in `astro.config.mjs` before deployment. 

## ⚙️ Frontmatter of Posts

```yaml
---
title: My First Blog Post
published: 2023-09-09
description: This is the first post of my new Astro blog.
image: /images/cover.jpg
tags: [Foo, Bar]
category: Front-end
draft: false
---
```

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                             | Action                                           |
|:------------------------------------|:-------------------------------------------------|
| `pnpm install` AND `pnpm add sharp` | Installs dependencies                            |
| `pnpm dev`                          | Starts local dev server at `localhost:4321`      |
| `pnpm build`                        | Build your production site to `./dist/`          |
| `pnpm preview`                      | Preview your build locally, before deploying     |
| `pnpm new-post <filename>`          | Create a new post                                |
| `pnpm astro ...`                    | Run CLI commands like `astro add`, `astro check` |
| `pnpm astro --help`                 | Get help using the Astro CLI                     |
