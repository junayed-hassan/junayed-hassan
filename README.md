
<div align="right" >
<img  src="https://visitor-badge.laobi.icu/badge?page_id=junayed-hassan" />
</div>

<div align="left" >
    <a href="https://github.com/junayed-hassan" target="_blank">
    <img src="https://img.shields.io/github/followers/junayed-hassan?label=Follow&style=social" alt="GitHub Follow">
  </a>
</div>

<h1 align="center">
    <img src="https://readme-typing-svg.herokuapp.com/?font=Righteous&size=40&center=true&vCenter=true&width=600&height=80&duration=5000&lines=Hey+there!+👋;+I'm+junayde+hassan!" />
</h1>



<h3 align="center">
  A passionate web developer from <span style="color: yellow;">Bangladesh</span> 🚀
</h3>



<br/>

<div align="center">

🔭 I’m currently working on **Frontend Development**

🌱 I’m currently learning **MERN Stack** 

💬 Ask me about **Node.js, React, Firebase... or anything 
[here](https://github.com/junayed-hassan)** 

⚡ Fun fact: **Game of Thrones Night's Watch cloaks are made from IKEA rugs**! 😱🧣



</div>

<br/>

<div align="center"> 
    <a href="mailto:junayed-hassan@gmail.com">
        <img src="https://img.shields.io/badge/Gmail-333333?style=for-the-badge&logo=gmail&logoColor=red" />
    </a>
    <a href="https://www.linkedin.com/in/junayed-hassan/" target="_blank">
        <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
    </a>
    <a href="https://github.com/junayed-hassan" target="_blank">
        <img src="https://img.shields.io/badge/Portfolio-FF5722?style=for-the-badge&logo=todoist&logoColor=white" />
    </a>
</div>

<hr/>

<h2 align="center">⚒️ Languages-Frameworks-Tools ⚒️</h2>
<br/>
<div align="center">
    <img src="https://skillicons.dev/icons?i=react,bootstrap,mui,html,css,vscode,github,figma,tailwind,git,r" />
    <img src="https://skillicons.dev/icons?i=nodejs,python,javascript,typescript,express,firebase,mongodb,nextjs,mysql,flask" /><br>
</div>

<div align="center">
    <h4>Made with ❤️ by <strong>junayed-hassan</strong></h4>
</div>


name: GitHub Snake Game

on:
  schedule:
    # প্রতি ৬ ঘণ্টা পর পর রান করার জন্য শিডিউল
    - cron: "0 */6 * * *"
  workflow_dispatch: # ম্যানুয়ালি ট্রিগার করার অপশন
  push:
    branches:
      - main # মেইন ব্রাঞ্চে পুশ করলে রান করবে

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      
      - name: Checkout Repository
        uses: actions/checkout@v3
      
     
      - name: Generate Snake Game
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark
            dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      
     
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
          publish_branch: output
          commit_message: "Update snake game animation [skip ci]"

