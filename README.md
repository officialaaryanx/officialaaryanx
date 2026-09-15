<style>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;600&display=swap');

:root {
  --terminal-bg: #0a0a0f;
  --terminal-green: #00ff41;
  --terminal-cyan: #00ffff;
  --terminal-magenta: #ff00ff;
  --terminal-red: #ff0040;
  --terminal-yellow: #ffd700;
  --terminal-dark: #0d1117;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: var(--terminal-bg);
  font-family: 'Fira Code', 'Courier New', monospace;
}

/* Matrix Rain Effect */
.matrix-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  opacity: 0.15;
  background: linear-gradient(180deg, transparent 0%, var(--terminal-green) 100%);
  animation: matrixPulse 8s ease-in-out infinite;
}

@keyframes matrixPulse {
  0%, 100% { opacity: 0.15; }
  50% { opacity: 0.25; }
}

/* Glitch Effect */
.glitch {
  position: relative;
  animation: glitch-skew 3s infinite linear alternate-reverse;
  color: var(--terminal-green);
  text-shadow: 
    0 0 10px var(--terminal-green),
    0 0 20px var(--terminal-green),
    0 0 40px var(--terminal-green),
    2px 0 0 var(--terminal-red),
    -2px 0 0 var(--terminal-cyan);
}

@keyframes glitch-skew {
  0% { transform: skew(0deg); }
  20% { transform: skew(-1deg); }
  40% { transform: skew(1deg); }
  60% { transform: skew(-0.5deg); }
  80% { transform: skew(0.5deg); }
  100% { transform: skew(0deg); }
}

/* Typing Animation */
.typing {
  overflow: hidden;
  border-right: .15em solid var(--terminal-green);
  white-space: nowrap;
  margin: 0 auto;
  letter-spacing: .15em;
  animation: 
    typing 3.5s steps(40, end),
    blink-caret .75s step-end infinite;
}

@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: var(--terminal-green) }
}

/* Terminal Window */
.terminal {
  background: var(--terminal-dark);
  border: 2px solid var(--terminal-green);
  border-radius: 8px;
  box-shadow: 
    0 0 20px rgba(0, 255, 65, 0.5),
    inset 0 0 20px rgba(0, 255, 65, 0.1);
  overflow: hidden;
  margin: 20px 0;
}

.terminal-header {
  background: linear-gradient(90deg, #1a1a2e 0%, #16213e 100%);
  padding: 10px 15px;
  display: flex;
  align-items: center;
  border-bottom: 1px solid var(--terminal-green);
}

.terminal-buttons {
  display: flex;
  gap: 8px;
}

.terminal-btn {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  display: inline-block;
}

.terminal-btn.red { background: var(--terminal-red); }
.terminal-btn.yellow { background: var(--terminal-yellow); }
.terminal-btn.green { background: var(--terminal-green); }

.terminal-title {
  flex: 1;
  text-align: center;
  color: var(--terminal-green);
  font-size: 0.9em;
  letter-spacing: 2px;
}

.terminal-body {
  padding: 20px;
  color: var(--terminal-green);
  font-family: 'Fira Code', monospace;
  font-size: 0.9em;
  line-height: 1.6;
}

.terminal-body .prompt {
  color: var(--terminal-cyan);
  font-weight: 600;
}

.terminal-body .command {
  color: var(--terminal-yellow);
}

.terminal-body .output {
  color: var(--terminal-green);
  opacity: 0.9;
}

.terminal-body .comment {
  color: #6a737d;
  font-style: italic;
}

/* Scanning Line */
.scanline {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, 
    transparent 0%, 
    var(--terminal-green) 50%, 
    transparent 100%);
  opacity: 0.3;
  animation: scanline 4s linear infinite;
  z-index: 1000;
  pointer-events: none;
}

@keyframes scanline {
  0% { top: 0%; }
  100% { top: 100%; }
}

/* Section Animations */
.section {
  opacity: 0;
  animation: fadeInUp 0.8s ease-out forwards;
  margin: 40px 0;
}

.section:nth-child(1) { animation-delay: 0.2s; }
.section:nth-child(2) { animation-delay: 0.4s; }
.section:nth-child(3) { animation-delay: 0.6s; }
.section:nth-child(4) { animation-delay: 0.8s; }

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Neon Glow Effects */
.neon-text {
  color: var(--terminal-green);
  text-shadow: 
    0 0 5px var(--terminal-green),
    0 0 10px var(--terminal-green),
    0 0 20px var(--terminal-green),
    0 0 40px var(--terminal-green);
  animation: neon-flicker 3s infinite alternate;
}

@keyframes neon-flicker {
  0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% {
    text-shadow: 
      0 0 5px var(--terminal-green),
      0 0 10px var(--terminal-green),
      0 0 20px var(--terminal-green),
      0 0 40px var(--terminal-green);
  }
  20%, 24%, 55% {
    text-shadow: none;
  }
}

/* Progress Bar Animation */
.progress-bar {
  height: 20px;
  background: linear-gradient(90deg, 
    var(--terminal-green) 0%, 
    var(--terminal-cyan) 50%, 
    var(--terminal-magenta) 100%);
  background-size: 200% 100%;
  animation: gradient-shift 3s ease infinite;
  border-radius: 3px;
  position: relative;
  overflow: hidden;
}

@keyframes gradient-shift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.progress-bar::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 255, 255, 0.3),
    transparent
  );
  animation: shimmer 2s infinite;
}

@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

/* Cursor Blink */
.cursor {
  display: inline-block;
  width: 10px;
  height: 1.2em;
  background: var(--terminal-green);
  margin-left: 5px;
  vertical-align: text-bottom;
  animation: blink 1s step-end infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

/* Hacker Border */
.hacker-border {
  border: 1px solid var(--terminal-green);
  box-shadow: 
    0 0 10px rgba(0, 255, 65, 0.3),
    inset 0 0 10px rgba(0, 255, 65, 0.1);
  padding: 15px;
  margin: 10px 0;
  position: relative;
}

.hacker-border::before {
  content: '>';
  position: absolute;
  top: -10px;
  left: 10px;
  background: var(--terminal-bg);
  padding: 0 5px;
  color: var(--terminal-green);
  font-weight: bold;
}

/* ASCII Art Styling */
.ascii-art {
  color: var(--terminal-cyan);
  font-size: 0.85em;
  line-height: 1.2;
  text-shadow: 0 0 5px var(--terminal-cyan);
  animation: ascii-glow 2s ease-in-out infinite alternate;
}

@keyframes ascii-glow {
  from { opacity: 0.8; }
  to { opacity: 1; }
}

/* Stats Cards Enhancement */
.stats-card {
  border: 1px solid var(--terminal-green);
  border-radius: 8px;
  padding: 15px;
  margin: 10px 0;
  background: rgba(0, 255, 65, 0.05);
  box-shadow: 
    0 0 15px rgba(0, 255, 65, 0.2),
    inset 0 0 15px rgba(0, 255, 65, 0.05);
  transition: all 0.3s ease;
}

.stats-card:hover {
  transform: translateY(-5px);
  box-shadow: 
    0 5px 25px rgba(0, 255, 65, 0.4),
    inset 0 0 20px rgba(0, 255, 65, 0.1);
}

/* Badge Animation */
.badge {
  transition: all 0.3s ease;
  filter: drop-shadow(0 0 5px var(--terminal-green));
}

.badge:hover {
  transform: scale(1.1);
  filter: drop-shadow(0 0 10px var(--terminal-cyan));
}

/* Divider Animation */
.divider {
  height: 2px;
  background: linear-gradient(90deg, 
    transparent 0%, 
    var(--terminal-green) 50%, 
    transparent 100%);
  margin: 30px 0;
  animation: divider-pulse 2s ease-in-out infinite;
}

@keyframes divider-pulse {
  0%, 100% { opacity: 0.5; }
  50% { opacity: 1; }
}

/* Responsive */
@media (max-width: 768px) {
  .terminal-body {
    font-size: 0.8em;
  }
  
  .ascii-art {
    font-size: 0.7em;
  }
}
</style>

<div class="matrix-bg"></div>
<div class="scanline"></div>

<div align="center">

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">root@officialaaryanx:~</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="command">whoami</span><br><br>
    <span class="output">
╔═══════════════════════════════════════════════╗<br>
║  👤 USER:       officialaaryanx               ║<br>
║  🎯 ROLE:       Frontend Developer // OSS     ║<br>
║  ⚡ STATUS:     [████████████████████] ONLINE ║<br>
║  🎮 MODE:       HACKER_THEME_v2.0            ║<br>
╚═══════════════════════════════════════════════╝<span class="cursor"></span>
    </span>
  </div>
</div>

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">/proc/motd</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="command">cat /proc/motd</span><br><br>
    <span class="output">
> "The best way to predict the future<br>
>  is to invent it." — Alan Kay
    </span>
  </div>
</div>

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">neofetch</div>
  </div>
  <div class="terminal-body">
    <pre class="ascii-art">
        .--.         officialaaryanx@github
       |o_o |        ----------------------
       |:_/ |        OS: Web & Open Source
      //   \ \       Host: GitHub Pages
     (|     | )      Kernel: JS/PHP/Python
    /'\_   _/`\      Shell: bash
    \___)=(___/      Theme: Hacker // Radical
    </pre>
  </div>
</div>

</div>

---

<div class="section">
<div align="center">

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">cat about_me.txt</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="command">cat about_me.txt</span><br><br>
  </div>
</div>

</div>

# 💫 About Me:
🔭 I’m currently working on building responsive web apps and polishing frontend performance, turning design ideas into functional websites.<br>👯 I’m looking to collaborate on open-source projects (beginner-friendly welcome 🙌), student-led tech communities and events.<br>🤝 I’m looking for help with open-source contribution workflows, backend integration with frontend apps.<br>🌱 I’m currently learning advanced JavaScript concepts, PHP, and a lot of things altogether.<br>💬 Ask me about HTML, CSS, and JavaScript fundamentals, responsive layouts and CSS tricks.<br>⚡ Fun fact <code>console.log</code> is still my best friend
</div>

<div class="section">
<div align="center">

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">cat skills.log</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="command">cat skills.log</span><br><br>
  </div>
</div>

</div>

# 💻 Tech Stack:
<div class="stats-card">
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white) 
![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white) 
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) 
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) 
![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white) 
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) 
![Bootstrap](https://img.shields.io/badge/bootstrap-%238511FA.svg?style=for-the-badge&logo=bootstrap&logoColor=white) 
![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=for-the-badge&logo=apache&logoColor=white) 
![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white) 
![Figma](https://img.shields.io/badge/figma-%23F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white) 
![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white) 
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
</div>
</div>

<div class="section">
<div align="center">

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">./stats --verbose</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="command">./stats --verbose</span><br><br>
  </div>
</div>

</div>

# 📊 GitHub Stats:
<div class="stats-card">
![](https://github-readme-stats.vercel.app/api?username=officialaaryanx&theme=radical&hide_border=false&include_all_commits=false&count_private=false)<br/>
![](https://nirzak-streak-stats.vercel.app/?user=officialaaryanx&theme=radical&hide_border=false)<br/>
![](https://github-readme-stats.vercel.app/api/top-langs/?username=officialaaryanx&theme=radical&hide_border=false&include_all_commits=false&count_private=false&layout=compact)
</div>
</div>

<div class="section">
<div align="center">

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">sudo ./achievements.run</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="command">sudo ./achievements.run</span><br><br>
  </div>
</div>

</div>

## 🏆 GitHub Trophies
<div class="stats-card">
![](https://github-profile-trophy.vercel.app/?username=officialaaryanx&theme=radical&no-frame=false&no-bg=false&margin-w=4)
</div>
</div>

<div class="section">
<div align="center">

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">fortune | cowsay</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="command">fortune | cowsay</span><br><br>
  </div>
</div>

</div>

### ✍️ Random Dev Quote
<div class="stats-card">
![](https://quotes-github-readme.vercel.app/api?type=vetical&theme=radical)
</div>
</div>

<div class="divider"></div>

<div align="center">

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">status</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="command">echo "[ MISSION ACCOMPLISHED ]"</span><br><br>
    <span class="output">
████████████████████████████████████████<br>
█                                    █<br>
█   ALL SYSTEMS OPERATIONAL          █<br>
█   READY FOR NEXT MISSION           █<br>
█                                    █<br>
████████████████████████████████████████
    </span>
  </div>
</div>

</div>

[![](https://visitcount.itsvg.in/api?id=officialaaryanx&icon=2&color=0)](https://visitcount.itsvg.in)

<div align="center">

<div class="terminal">
  <div class="terminal-header">
    <div class="terminal-buttons">
      <span class="terminal-btn red"></span>
      <span class="terminal-btn yellow"></span>
      <span class="terminal-btn green"></span>
    </div>
    <div class="terminal-title">root@github:~$</div>
  </div>
  <div class="terminal-body">
    <span class="prompt">$</span> <span class="cursor"></span>
  </div>
</div>

</div>

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
