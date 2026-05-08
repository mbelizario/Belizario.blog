---
title: "Why I Created a Blog in 2026 and How I Built It"
date: 2026-05-08
draft: false
showToc: true
TocOpen: true
translationKey: blog-2026
tags: ["hugo", "blog", "writing", "learning"]
---

## Blogging in 2026

Creating a blog in 2026 might sound outdated or even pointless, but for me, this is a personal project that had been postponed for years and that I finally managed to bring to life.

I’m not trying to build an audience or monetize anything here. The blog will help me study. I plan to use it as a backup/documentation hub for everything I learn so I can revisit it whenever needed. As a bonus, it also helps me improve my writing.

## A Project Delayed for Years

This project was postponed for a long time because I kept overcomplicating something that could (and should) have been simple.

The main goal was always to write and document whatever I was studying, but creating the blog always got stuck on the decision of how to build it. Should I create the whole system from scratch or use an existing blog engine?

The truth is: the stack barely matters. What matters is studying and writing.

So the advice I can give is: **keep it simple**.

## Why Start Bilingual from Day One

Besides choosing the stack, another question that always remained unanswered — and delayed the beginning of the blog — was deciding which language I should write in. Portuguese to improve my writing or English to practice a “new” language?

Since I now want something simple, something I can just sit down and write without much ceremony, Portuguese was the obvious choice. Still, having the content available in a universal language feels almost mandatory nowadays.

To achieve that without turning it into another obstacle in the workflow, I followed something I saw in this [article](https://akitaonrails.com/2026/04/09/20-anos-de-blog-o-ano-em-que-a-ia-finalmente-me-deixou-traduzir-tudo/) and I plan to use LLMs for translation. My role is basically reviewing the translated text afterward.

To read the original Brazilian Portuguese version, just click “PT” at the top of the page.

## How I Built It

Given the context, let’s get into the technical side, detailing which tools I used, where the blog is hosted, and what the workflow for writing a post looks like. I was heavily influenced by this other [article](https://akitaonrails.com/2025/09/10/meu-novo-blog-como-eu-fiz/) from Akita as well.

### Hugo

Based on the article, I took a look at [Hugo](https://themes.gohugo.io/), which is basically a static site generator packed with several built-in features, such as multilingual support, search bars, breadcrumbs, and more.

The process was incredibly simple and matched exactly what I was looking for. I picked a [theme](https://themes.gohugo.io/themes/hugo-papermod/), read the documentation, and that was it. No unnecessary complexity.

### Setting Up the Environment

Since Git was already installed on my machine, I followed this [documentation](https://gohugo.io/getting-started/quick-start/) and the whole process basically came down to:

1. Create a repository on GitHub and clone it locally -> The entire source code is available [here](https://github.com/mbelizario/Belizario.blog).

2. Install ***PowerShell***

```powershell
winget install --id Microsoft.PowerShell --source winget
```

3. Install Hugo directly through ***PowerShell***

```powershell
winget install Hugo.Hugo.Extended
```

4. Still using ***PowerShell***, navigate to the root folder of the repository cloned in step 1 and run:

```powershell
hugo new project Belizario.blog --format yaml --force
```

From this point on, the work was basically customization — choosing the theme and deciding which features I wanted enabled or disabled. I followed the documentation available [here](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation), and most of the result can be seen in the [hugo.yaml](https://github.com/mbelizario/Belizario.blog/blob/setup-inicial/hugo.yaml) file in my repository.

### Deploy

Once the blog was running locally, it was time to decide how deployment would work, and I tried to keep it as practical as possible.

I created an account and a project on [Netlify](https://www.netlify.com/), then simply imported my GitHub repository and configured a few settings.

Under ***Project configuration*** -> ***Branches and deploy contexts*** -> ***Configure***:

- Production branch: "master"
- Branch deploys: "Deploy only the production branch"
- Deploy Previews: "Don’t deploy pull requests"

I also had to go to ***Project configuration*** -> ***Build & deploy*** -> ***Build settings*** -> ***Configure*** and define:

- Base directory = "/"
- Build command = "Hugo"
- Publish directory = "public"

Since the site is extremely simple — no database or anything like that — the cost on Netlify is ZERO.

The workflow ended up being incredibly simple: I just create a branch in my repository, write the post in a `.md` file using any text editor (currently VS Code), and once it’s ready, I merge it into `master`, which automatically triggers the deployment on Netlify. Zero headaches.