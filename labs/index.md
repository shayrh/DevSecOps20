---
layout: default
title: DevSecOps Labs
---

# DevSecOps Labs

Welcome to the DevSecOps course labs! Click on any lab category below to explore the available exercises and materials.

<style>
.lab-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    margin: 30px 0;
}

.lab-card {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 15px;
    padding: 25px;
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 8px 25px rgba(0,0,0,0.15);
    position: relative;
    overflow: hidden;
}

.lab-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 15px 35px rgba(0,0,0,0.2);
}

.lab-card h3 {
    margin: 0 0 15px 0;
    font-size: 1.5em;
    font-weight: 600;
}

.lab-card p {
    margin: 0;
    opacity: 0.9;
    line-height: 1.5;
}

.lab-files {
    background: rgba(255,255,255,0.1);
    border-radius: 10px;
    padding: 15px;
    margin-top: 15px;
    backdrop-filter: blur(10px);
}

.lab-files h4 {
    margin: 0 0 10px 0;
    font-size: 1.1em;
    color: #fff;
}

.file-list {
    list-style: none;
    padding: 0;
    margin: 0;
}

.file-list li {
    padding: 8px 12px;
    margin: 5px 0;
    background: rgba(255,255,255,0.1);
    border-radius: 6px;
    border-left: 3px solid #fff;
    transition: all 0.2s ease;
}

.file-list li:hover {
    background: rgba(255,255,255,0.2);
    transform: translateX(5px);
}

.file-list a {
    color: white;
    text-decoration: none;
    display: block;
}

.file-list a:hover {
    text-decoration: underline;
}

.empty-folder {
    font-style: italic;
    opacity: 0.7;
    padding: 10px;
    text-align: center;
}

.lab-icon {
    font-size: 2em;
    margin-bottom: 10px;
    display: block;
}

@media (max-width: 768px) {
    .lab-container {
        grid-template-columns: 1fr;
    }
    
    .lab-card {
        padding: 20px;
    }
}
</style>

<div class="lab-container">

<div class="lab-card">
    <span class="lab-icon">🐧</span>
    <h3>Linux Basics</h3>
    <p>Master essential Linux commands, file systems, and system administration fundamentals.</p>
    <div class="lab-files">
        <h4>Available Labs:</h4>
        <ul class="file-list">
            <li><a href="linux-basics/linux-basics-1.md">Linux Basics 1 - Introduction to Linux</a></li>
            <li><a href="linux-basics/linux-basics-2.md">Linux Basics 2 - Advanced Commands</a></li>
        </ul>
    </div>
</div>

<div class="lab-card">
    <span class="lab-icon">📊</span>
    <h3>Monitoring</h3>
    <p>Learn about system monitoring, logging, and observability tools and practices.</p>
    <div class="lab-files">
        <h4>Available Labs:</h4>
        <ul class="file-list">
            <li class="empty-folder">Coming Soon - Labs in development</li>
        </ul>
    </div>
</div>

<div class="lab-card">
    <span class="lab-icon">☸️</span>
    <h3>Kubernetes</h3>
    <p>Explore container orchestration with Kubernetes, deployments, and cluster management.</p>
    <div class="lab-files">
        <h4>Available Labs:</h4>
        <ul class="file-list">
            <li class="empty-folder">Coming Soon - Labs in development</li>
        </ul>
    </div>
</div>

<div class="lab-card">
    <span class="lab-icon">🐳</span>
    <h3>Docker</h3>
    <p>Containerize applications with Docker, build images, and manage containers effectively.</p>
    <div class="lab-files">
        <h4>Available Labs:</h4>
        <ul class="file-list">
            <li class="empty-folder">Coming Soon - Labs in development</li>
        </ul>
    </div>
</div>

<div class="lab-card">
    <span class="lab-icon">🏗️</span>
    <h3>Terraform</h3>
    <p>Infrastructure as Code with Terraform, provisioning cloud resources programmatically.</p>
    <div class="lab-files">
        <h4>Available Labs:</h4>
        <ul class="file-list">
            <li class="empty-folder">Coming Soon - Labs in development</li>
        </ul>
    </div>
</div>

<div class="lab-card">
    <span class="lab-icon">🐍</span>
    <h3>Python</h3>
    <p>Automate tasks and build tools with Python scripting for DevOps workflows.</p>
    <div class="lab-files">
        <h4>Available Labs:</h4>
        <ul class="file-list">
            <li class="empty-folder">Coming Soon - Labs in development</li>
        </ul>
    </div>
</div>

<div class="lab-card">
    <span class="lab-icon">📝</span>
    <h3>Git & GitHub</h3>
    <p>Version control with Git, collaborative development, and GitHub workflows.</p>
    <div class="lab-files">
        <h4>Available Labs:</h4>
        <ul class="file-list">
            <li class="empty-folder">Coming Soon - Labs in development</li>
        </ul>
    </div>
</div>

<div class="lab-card">
    <span class="lab-icon">💻</span>
    <h3>Bash Scripting</h3>
    <p>Automate system tasks and create powerful shell scripts for DevOps automation.</p>
    <div class="lab-files">
        <h4>Available Labs:</h4>
        <ul class="file-list">
            <li class="empty-folder">Coming Soon - Labs in development</li>
        </ul>
    </div>
</div>

</div>

## Getting Started

1. **Choose a lab category** that interests you from the cards above
2. **Click on any lab file** to access the detailed instructions
3. **Follow the step-by-step guides** to complete hands-on exercises
4. **Practice regularly** to reinforce your learning

## Lab Categories Overview

- **Linux Basics**: Essential commands and system administration
- **Monitoring**: System observability and logging
- **Kubernetes**: Container orchestration and management
- **Docker**: Containerization and image management
- **Terraform**: Infrastructure as Code
- **Python**: Automation and scripting
- **Git & GitHub**: Version control and collaboration
- **Bash Scripting**: Shell automation and scripting

---

_Note: Some labs are currently in development. Check back regularly for new content!_
