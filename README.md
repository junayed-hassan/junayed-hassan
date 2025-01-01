
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










const axios = require('axios');
const fs = require('fs');

const WAKATIME_API_KEY = process.env.WAKATIME_API_KEY;
const WAKATIME_API_URL = `https://wakatime.com/api/v1/users/current/stats/last_7_days?api_key=${WAKATIME_API_KEY}`;

async function fetchWakaTimeStats() {
  try {
    const response = await axios.get(WAKATIME_API_URL);
    const data = response.data.data;

    const stats = `
# WakaTime Stats for Last 7 Days

## 🕒 Time Spent on Projects:
${data.projects
  .map((project) => `- ${project.name}: ${project.text}`)
  .join('\n')}

## 📂 Languages Used:
${data.languages
  .map((language) => `- ${language.name}: ${language.text}`)
  .join('\n')}
    `;

    fs.writeFileSync('WakaTimeStats.md', stats);
    console.log('WakaTime stats updated successfully!');
  } catch (error) {
    console.error('Error fetching WakaTime stats:', error.message);
  }
}

fetchWakaTimeStats();

