---
layout: about
title: about
permalink: /
subtitle: PhD Student @ <a href="https://spectrum-lab-iisc.github.io" target="_blank" rel="noopener">Spectrum Lab</a>, <a href="http://iisc.ac.in" target="_blank" rel="noopener">Indian Institute of Science</a>

profile:
    align: right
    image: Abijith.jpg
    image_circular: false # crops the image to make it circular
    more_info: >

news: true # includes a list of news items
latest_posts: true # includes a list of the newest posts
selected_papers: true # includes a list of papers marked as "selected={true}"
social: false # includes social icons at the bottom of the page
---

<div class="intro-section">
    <div class="intro-content">
        <div class="intro-highlight">
            <i class="fas fa-rocket"></i>
            <span>Research Focus</span>
        </div>
        <p class="intro-text">
            <strong>Challenging the frontiers of<br>computational imaging.</strong>
        </p>
        <p class="intro-description">
            I work in the intersection of sampling theory, inverse problems and machine learning for event-driven imaging &mdash; <em>with high resolution, speed and dynamic range!</em>
        </p>
        <div class="intro-background">
            <i class="fas fa-university"></i>
            <span>Previously at <a href="https://www.nitk.ac.in" target="_blank" rel="noopener">National Institute of Technology Karnataka</a>.</span>    </div>
    </div>
</div>

<!-- Dynamic Fourier Descriptors / Unlimited Sampling Plot -->
<div id="hero-canvas-container" style="width:100%; height: 300px; margin-bottom: 1rem; position: relative; overflow: hidden;">
    <canvas id="hero-canvas"></canvas>
</div>

<script>
(function() {
    const canvas = document.getElementById('hero-canvas');
    const ctx = canvas.getContext('2d');
    
    let width, height;
    
    function resize() {
        width = canvas.parentElement.clientWidth;
        height = canvas.parentElement.clientHeight;
        canvas.width = width;
        canvas.height = height;
    }
    
    window.addEventListener('resize', resize);
    resize();
    
    const colors = {
        theme: '#E30613',
        text: '#000000',
        grid: '#e0e0e0'
    };
    
    const threshold = 60;
    const wave = [];
    const rawWave = [];
    const maxWavePoints = 20000;
    let time = 0;
    
    // State for neusamp logic
    let y_prev = null;
    let currentOffset = 0;
    
    function draw() {
        ctx.clearRect(0, 0, width, height);
        
        const cy = height / 2; // Center Y
        
        // Calculate signal value (Sum of Sinusoids)
        let rawSignal = 60 * Math.sin(time * 1.0) + 
                        40 * Math.sin(time * 1.618) + 
                        20 * Math.sin(time * 2.718);
        
        // Apply "Reset" logic (neusamp)
        if (y_prev === null) {
            y_prev = rawSignal;
        }

        let z = rawSignal - y_prev;
        
        if (z >= threshold) {
            currentOffset += threshold;
            y_prev = rawSignal;
        } else if (z <= -threshold) {
            currentOffset -= threshold;
            y_prev = rawSignal;
        }
        
        let processedSignal = rawSignal - currentOffset;
        
        // Store wave point
        wave.unshift(processedSignal);
        rawWave.unshift(rawSignal);
        if (wave.length > maxWavePoints) {
            wave.pop();
            rawWave.pop();
        }
        
        const waveStartX = 50;
        
        // Draw Threshold Lines
        ctx.beginPath();
        ctx.strokeStyle = 'rgba(0,0,0,0.1)';
        ctx.setLineDash([5, 5]);
        ctx.moveTo(waveStartX, cy - threshold);
        ctx.lineTo(width, cy - threshold);
        ctx.moveTo(waveStartX, cy + threshold);
        ctx.lineTo(width, cy + threshold);
        ctx.stroke();
        ctx.setLineDash([]);
        
        // Draw Raw Wave
        ctx.beginPath();
        ctx.strokeStyle = 'rgba(0,0,0,0.15)';
        ctx.lineWidth = 2;
        
        for (let i = 0; i < rawWave.length; i++) {
            const px = waveStartX + i * 1.5;
            const py = cy + rawWave[i];
            
            if (px > width) break;
            
            if (i === 0) ctx.moveTo(px, py);
            else ctx.lineTo(px, py);
        }
        ctx.stroke();

        // Draw Folded Wave
        ctx.beginPath();
        ctx.strokeStyle = colors.theme;
        ctx.lineWidth = 2;
        
        for (let i = 0; i < wave.length; i++) {
            const px = waveStartX + i * 1.5; // Spacing
            const py = cy + wave[i];
            
            if (px > width) break;
            
            // Handle jumps (don't draw line across the jump)
            if (i > 0) {
                const prevPy = cy + wave[i-1];
                if (Math.abs(py - prevPy) > threshold * 0.8) {
                    ctx.stroke();
                    ctx.beginPath();
                }
            }
            
            if (i === 0) ctx.moveTo(px, py);
            else ctx.lineTo(px, py);
        }
        ctx.stroke();
        
        time += 0.02;
        requestAnimationFrame(draw);
    }
    
    draw();
})();
</script>

<style>
/* Enhanced Intro Section */
.intro-section {
  padding: 0;
  margin: 2rem 0;
  position: relative;
}

.intro-content {
  max-width: 700px;
  margin: 0 auto;
}

.intro-highlight {
  display: inline-flex;
  align-items: center;
  background: transparent;
  color: var(--global-theme-color);
  padding: 0;
  border-radius: 0;
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.intro-highlight i {
  margin-right: 0.5rem;
}

.intro-text {
  font-size: 1.3rem;
  line-height: 1.4;
  color: var(--global-text-color);
  margin-bottom: 1.2rem;
}

.intro-description {
  font-size: 1.1rem;
  line-height: 1.6;
  color: var(--global-text-color-light);
  margin-bottom: 1.5rem;
}

.intro-background {
  display: flex;
  align-items: center;
  font-size: 0.95rem;
  color: var(--global-text-color-light);
  padding: 0;
  background-color: transparent;
  border: none;
}

.intro-background i {
  margin-right: 0.5rem;
  color: var(--global-theme-color);
}

/* Responsive design */
@media (max-width: 768px) {
  .intro-section {
    margin: 1.5rem 0;
  }
  
  .intro-text {
    font-size: 1.2rem;
  }
  
  .intro-description {
    font-size: 1rem;
  }
}

@media (max-width: 600px) {
  .intro-text {
    font-size: 1.1rem;
  }
  
  .intro-description {
    font-size: 0.95rem;
  }
}
</style>
