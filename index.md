---
layout: default
title: "DevSecOps 20 "
description: "Master DevSecOps with cutting-edge labs, real-world projects, and advanced cybersecurity practices"
---

<div class="cyber-background"></div>
<div class="floating-particles">
  <div class="particle" style="left: 10%; animation-delay: 0s;"></div>
  <div class="particle" style="left: 20%; animation-delay: 1s;"></div>
  <div class="particle" style="left: 30%; animation-delay: 2s;"></div>
  <div class="particle" style="left: 40%; animation-delay: 3s;"></div>
  <div class="particle" style="left: 50%; animation-delay: 4s;"></div>
  <div class="particle" style="left: 60%; animation-delay: 5s;"></div>
  <div class="particle" style="left: 70%; animation-delay: 0.5s;"></div>
  <div class="particle" style="left: 80%; animation-delay: 1.5s;"></div>
  <div class="particle" style="left: 90%; animation-delay: 2.5s;"></div>
  <div class="particle" style="left: 15%; animation-delay: 6s;"></div>
  <div class="particle" style="left: 25%; animation-delay: 7s;"></div>
  <div class="particle" style="left: 35%; animation-delay: 8s;"></div>
  <div class="particle" style="left: 45%; animation-delay: 9s;"></div>
  <div class="particle" style="left: 55%; animation-delay: 10s;"></div>
  <div class="particle" style="left: 65%; animation-delay: 11s;"></div>
  <div class="particle" style="left: 75%; animation-delay: 12s;"></div>
  <div class="particle" style="left: 85%; animation-delay: 13s;"></div>
  <div class="particle" style="left: 95%; animation-delay: 14s;"></div>
</div>


<header style="text-align:center; margin-top:3rem; margin-bottom:2rem;">
  <h1 class="glitch" data-text="DEVSECOPS 20" style="font-size:3.5rem;">🛡️ DEVSECOPS 20</h1>
  <p style="color:var(--text-secondary); font-size:1.2rem; margin-top:1rem;">Elite Training Program for Modern Cybersecurity</p>
</header>


<section style="max-width:900px; margin:0 auto 3rem auto;">
  <h2 style="text-align:center; margin-bottom:2rem; background:var(--cyber-gradient); -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text; text-transform:uppercase; letter-spacing:2px;">Lessons</h2>
  <div class="course-modules">
    <div class="module" style="text-align:center;">
      <h3>🐧 Linux Basics</h3>
       <p>Master command-line warfare, file system navigation, permission matrices, and process control. Foundation for all cyber operations.</p>
      <a href="lessons/01-linux-basics/" class="btn btn-success">Start Lesson</a>
    </div>
    <br>
    <br>
     <div class="module" style="text-align:center;">
      <h3>🐧 Linux Basics 2 </h3>
            <p>File system navigation, and process control </p>
      <a href="lessons/02-linux-basics/" class="btn btn-success">Start Lesson</a>
      <a href="docs/linux-cheatsheet/" class="btn btn-success">cheatsheet</a>
    </div>
    <br>
    <br>
    <div class="module" style="text-align:center;">
      <h3>🐧 Linux Basics 2 </h3>
            <p>users permissions and binary </p>
      <a href="lessons/03-linux-basics/" class="btn btn-success">Start Lesson</a>
      <a href="lessons/03-linux-basics/cheatsheet.md" class="btn btn-success">cheatsheet</a>
    </div>
    <!--
    To add more lessons, copy the block above and update the folder and title.
    Example:
    <div class="module" style="text-align:center;">
      <h3>📜 Bash Scripting</h3>
      <p>Deploy automated bash protocols, handle system errors, and construct robust automation scripts for cyber warfare operations.</p>
      <a href="lessons/02-bash-scripting/" class="btn btn-success">Start Lesson</a>
    </div>
    -->
  </div>
</section>

---

<div style="text-align: center; color: var(--text-muted); margin: 3rem 0; font-family: monospace; border-top: 1px solid rgba(0, 245, 255, 0.2); padding-top: 2rem;">
  <strong style="color: var(--neon-blue);">[CLASSIFIED] DEVELOPED BY ELITE DEVSECOPS COMMAND</strong><br>
  <small>Last Security Update: July 2025 | Clearance Level: ULTRA | License: MIT</small>
</div>

<script>
// Ultra Enhanced interactive functionality for cyber theme
document.addEventListener('DOMContentLoaded', function() {
  // Enhanced progress bar animations with staggered timing
  const progressBars = document.querySelectorAll('.progress-fill');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, index) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          const randomProgress = Math.random() * 60 + 20; // 20-80%
          entry.target.style.width = randomProgress + '%';
          entry.target.style.animation = 'shimmer 2.5s infinite, gradientShift 3s ease-in-out infinite';
        }, index * 200);
      }
    });
  }, { threshold: 0.1 });
  
  progressBars.forEach(bar => observer.observe(bar));
  
  // Enhanced glitch effect with sound simulation
  const glitchElements = document.querySelectorAll('.glitch');
  glitchElements.forEach(el => {
    el.addEventListener('mouseenter', function() {
      this.style.animation = 'glitch-1 0.5s infinite, glitchFloat 0.5s infinite';
      this.style.filter = 'brightness(1.5) contrast(1.2)';
      setTimeout(() => {
        this.style.animation = '';
        this.style.filter = '';
      }, 1500);
    });
  });
  
  // Enhanced typing effect with cyber styling
  const progressText = document.querySelector('.progress-container p');
  if (progressText) {
    const originalText = progressText.textContent;
    progressText.textContent = '';
    let i = 0;
    const typeWriter = () => {
      if (i < originalText.length) {
        progressText.textContent += originalText.charAt(i);
        progressText.style.textShadow = `0 0 10px rgba(0, 245, 255, ${0.5 + Math.random() * 0.5})`;
        i++;
        setTimeout(typeWriter, 30);
      } else {
        progressText.style.textShadow = '0 0 20px rgba(0, 245, 255, 0.8)';
      }
    };
    setTimeout(typeWriter, 1000);
  }
  
  // Enhanced dynamic particle system
  function createParticle() {
    const particle = document.createElement('div');
    particle.className = 'particle';
    particle.style.left = Math.random() * 100 + '%';
    particle.style.top = Math.random() * 100 + '%';
    particle.style.animationDuration = (Math.random() * 4 + 4) + 's';
    particle.style.animationDelay = Math.random() * 2 + 's';
    
    // Random particle colors
    const colors = ['var(--neon-blue)', 'var(--neon-purple)', 'var(--neon-green)', 'var(--neon-pink)', 'var(--neon-yellow)'];
    particle.style.background = colors[Math.floor(Math.random() * colors.length)];
    
    document.querySelector('.floating-particles').appendChild(particle);
    
    setTimeout(() => {
      if (particle.parentNode) {
        particle.remove();
      }
    }, 8000);
  }
  
  // Create particles with varying intervals
  setInterval(createParticle, 1500);
  setInterval(() => createParticle(), 3000);
  
  // Enhanced button interactions
  const buttons = document.querySelectorAll('.btn');
  buttons.forEach(btn => {
    btn.addEventListener('mouseenter', function() {
      this.style.transform = 'translateY(-5px) scale(1.1)';
      this.style.boxShadow = '0 0 40px rgba(0, 245, 255, 0.8)';
    });
    
    btn.addEventListener('mouseleave', function() {
      this.style.transform = '';
      this.style.boxShadow = '';
    });
    
    btn.addEventListener('click', function() {
      // Create ripple effect
      const ripple = document.createElement('div');
      ripple.style.position = 'absolute';
      ripple.style.borderRadius = '50%';
      ripple.style.background = 'rgba(0, 245, 255, 0.6)';
      ripple.style.transform = 'scale(0)';
      ripple.style.animation = 'ripple 0.6s linear';
      ripple.style.left = '50%';
      ripple.style.top = '50%';
      ripple.style.width = '20px';
      ripple.style.height = '20px';
      ripple.style.marginLeft = '-10px';
      ripple.style.marginTop = '-10px';
      ripple.style.pointerEvents = 'none';
      
      this.appendChild(ripple);
      
      setTimeout(() => {
        ripple.remove();
      }, 600);
    });
  });
  
  // Add ripple animation
  const style = document.createElement('style');
  style.textContent = `
    @keyframes ripple {
      to {
        transform: scale(4);
        opacity: 0;
      }
    }
  `;
  document.head.appendChild(style);
  
  // Enhanced module hover effects
  const modules = document.querySelectorAll('.module');
  modules.forEach(module => {
    module.addEventListener('mouseenter', function() {
      this.style.transform = 'translateY(-20px) scale(1.05)';
      this.style.boxShadow = '0 0 50px rgba(0, 245, 255, 0.6)';
      this.style.borderColor = 'var(--neon-blue)';
    });
    
    module.addEventListener('mouseleave', function() {
      this.style.transform = '';
      this.style.boxShadow = '';
      this.style.borderColor = '';
    });
  });
  
  // Enhanced stat card interactions
  const statCards = document.querySelectorAll('.stat-card');
  statCards.forEach(card => {
    card.addEventListener('mouseenter', function() {
      this.style.transform = 'translateY(-15px) scale(1.08)';
      this.style.boxShadow = '0 0 60px rgba(0, 245, 255, 0.7)';
    });
    
    card.addEventListener('mouseleave', function() {
      this.style.transform = '';
      this.style.boxShadow = '';
    });
  });
  
  // Add parallax effect to background
  window.addEventListener('scroll', function() {
    const scrolled = window.pageYOffset;
    const parallax = document.querySelector('.cyber-background');
    if (parallax) {
      parallax.style.transform = `translateY(${scrolled * 0.5}px)`;
    }
  });
  
  // Add mouse tracking effect
  document.addEventListener('mousemove', function(e) {
    const particles = document.querySelectorAll('.particle');
    const mouseX = e.clientX / window.innerWidth;
    const mouseY = e.clientY / window.innerHeight;
    
    particles.forEach((particle, index) => {
      const speed = (index % 3 + 1) * 0.5;
      const x = (mouseX - 0.5) * speed * 20;
      const y = (mouseY - 0.5) * speed * 20;
      particle.style.transform += ` translate(${x}px, ${y}px)`;
    });
  });
  
  // Add cyber sound effects simulation (visual feedback)
  const links = document.querySelectorAll('a');
  links.forEach(link => {
    link.addEventListener('click', function(e) {
      // Create a brief flash effect
      const flash = document.createElement('div');
      flash.style.position = 'fixed';
      flash.style.top = '0';
      flash.style.left = '0';
      flash.style.width = '100%';
      flash.style.height = '100%';
      flash.style.background = 'rgba(0, 245, 255, 0.1)';
      flash.style.pointerEvents = 'none';
      flash.style.zIndex = '9999';
      flash.style.animation = 'flash 0.3s ease-out';
      
      document.body.appendChild(flash);
      
      setTimeout(() => {
        flash.remove();
      }, 300);
    });
  });
  
  // Add flash animation
  const flashStyle = document.createElement('style');
  flashStyle.textContent = `
    @keyframes flash {
      0% { opacity: 0; }
      50% { opacity: 1; }
      100% { opacity: 0; }
    }
  `;
  document.head.appendChild(flashStyle);
  
  // Enhanced table row interactions
  const tableRows = document.querySelectorAll('tr');
  tableRows.forEach(row => {
    row.addEventListener('mouseenter', function() {
      this.style.background = 'rgba(0, 245, 255, 0.15)';
      this.style.transform = 'scale(1.02)';
      this.style.boxShadow = '0 0 20px rgba(0, 245, 255, 0.3)';
    });
    
    row.addEventListener('mouseleave', function() {
      this.style.background = '';
      this.style.transform = '';
      this.style.boxShadow = '';
    });
  });
  
  // Add cyber loading animation
  window.addEventListener('load', function() {
    document.body.style.opacity = '0';
    document.body.style.transition = 'opacity 1s ease-in';
    
    setTimeout(() => {
      document.body.style.opacity = '1';
    }, 100);
  });
});
</script>
