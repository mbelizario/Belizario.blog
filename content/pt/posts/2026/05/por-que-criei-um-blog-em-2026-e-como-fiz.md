---
title: "Por que criei um blog em 2026 e como fiz"
date: 2026-05-08
draft: false
showToc: true
TocOpen: true
translationKey: blog-2026
tags: ["hugo", "blog", "escrita", "aprendizado"]
---

## Blog em 2026

Criar um blog em 2026 pode parecer ultrapassado ou até sem sentido, mas para mim, trata-se de um projeto pessoal que foi adiado por anos e que finalmente consegui tirar do papel. 

Não busco ter audiência ou monetizar aqui. O blog me ajudará nos estudos. Pretendo utilizá-lo como um backup/documentação de tudo que estudar para que eu possa revisitar sempre que necessário. De quebra, melhoro a minha escrita também.

## Projeto adiado por anos

Esse projeto foi postergado por muito tempo por eu complicar algo que poderia (e deveria) ser simples.

O objetivo principal sempre foi escrever e documentar o que eu estiver estudando, mas a criação do blog sempre esbarrava na decisão de como desenvolvê-lo. Criar um sistema do zero ou utilizar uma blog engine pronta? 

A verdade é que pouco importa a stack utilizada. O importante é estar estudando e escrevendo. 

Por isso, a dica que posso dar é **simplifique**.

## Por que já começar bilingue

Além da stack a ser utilizada, uma das dúvidas que sempre ficava sem resposta e atrasava o início do blog era em qual idioma eu deveria escrever. Português com o objetivo de melhorar a escrita ou inglês para treinar uma "nova" língua? 

Como agora eu quero algo simples, que eu possa sentar e escrever sem muita cerimônia, o português foi a escolha óbvia. No entanto, ter o conteúdo disponível em um idioma universal é algo indispensável atualmente. 

Para conseguir atingir esse objetivo sem que ele se transformasse em um empecilho no fluxo de trabalho, segui algo que vi neste [artigo](https://akitaonrails.com/2026/04/09/20-anos-de-blog-o-ano-em-que-a-ia-finalmente-me-deixou-traduzir-tudo/) e pretendo utilizar LLMs para traduzir. Fico apenas com o papel de fazer uma revisão sobre o texto traduzido.

Para ver a versão em inglês basta clicar em "EN" no topo da página.

## Como fiz

Dado o contexto, vamos à parte técnica, detalhando quais ferramentas foram utilizadas, onde o blog está hospedado e qual o fluxo de trabalho para escrever um post. Fui bastante influenciado por este [artigo](https://akitaonrails.com/2025/09/10/meu-novo-blog-como-eu-fiz/) também do Akita.

### Hugo

Baseado no artigo, dei uma olhada no [Hugo](https://themes.gohugo.io/), que nada mais é que um gerador de sites estáticos com várias funções já pré-definidas, como o suporte à traduções para outros idiomas, barra de pesquisa, breadcrumbs, entre outros.

Foi um processo bastante simples e que encaixou exatamente com o que eu procurava. Escolhi um [tema](https://themes.gohugo.io/themes/hugo-papermod/), li a documentação e é isso. Não tem frescura.

### Preparando o ambiente

Como eu já tinha o Git instalado na minha máquina, segui essa [documentação](https://gohugo.io/getting-started/quick-start/) e tudo se resumiu a:

1. Criar um repositório no Github e cloná-lo para a minha máquina local -> Todo o código está disponível [aqui](https://github.com/mbelizario/Belizario.blog).

2. Instalar o ***PowerShell***

```powershell
winget install --id Microsoft.PowerShell --source winget
```
3. Instalar o Hugo já via ***PowerShell***

```powershell
winget install Hugo.Hugo.Extended
```
4. Também via ***PowerShell*** fui na pasta raiz do repositório clonado no passo 1 e executei:

```powershell
hugo new project Belizario.blog --format yaml --force
```

A partir daqui o trabalho foi basicamente de customização, definindo o tema e as funcionalidades que queria deixar ativa ou não. Segui a documentação que está disponível [aqui](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation) e grande parte do resultado está no [hugo.yaml](https://github.com/mbelizario/Belizario.blog/blob/setup-inicial/hugo.yaml) do meu repositório.

### Deploy

Com o blog já funcionando em ambiente local, foi a hora de definir como seria o deploy e tentei deixá-lo o mais prático possível.

Criei uma conta e um projeto na [Netlify](https://www.netlify.com/), depois foi só importar o meu repositório do Github e definir algumas configurações.

Em ***Project configuration*** ->  ***Branches and deploy contexts*** -> ***Configure***:

- Production branch: "master"
- Branch deploys: "Deploy only the production branch"
- Deploy Previews: "Don’t deploy pull requests"

Além disso, precisei ir em ***Project configuration*** -> ***Build & deploy*** -> ***Build settings*** -> ***Configure*** e definir:

- Base directory = "/"
- Build command = "Hugo"
- Publish directory = "public"

Como é um site extremamente simples, sem banco de dados e nem nada do tipo, o custo é ZERO na Netlify. 

O processo de trabalho ficou extremamente simples, basta eu criar uma branch no meu repositório, escrever o post em um arquivo .md em qualquer editor de texto (atualmente estou usando o VS Code) e quando estiver pronto faço o merge na master, o que dispara automaticamente o deploy para a Netlify. Zero dor de cabeça.