<script setup>
const projects = [
  {
    ext: '.tsx',
    kind: 'keyword',
    name: 'note-taking-system',
    title: 'Adaptive Cloud-Based Note-Taking System',
    desc: 'Neurodiverse-centred, cloud-based note-taking platform to improve accessibility and focus for users with ADHD, applying AI summarisation and universal design for learning principles.',
    stack: ['React.js', 'Node.js (AWS Lambda)', 'DynamoDB', 'API Gateway', 'Cognito'],
    demo: '',
    repo: 'https://github.com/lesley-ayemi/adhd-notetaker-system'
  },
  {
    ext: '.sol',
    kind: 'function',
    name: 'blockchain-voting',
    title: 'Blockchain E-Voting System',
    desc: 'Secure, transparent e-voting platform using smart contracts to automate voter registration, vote casting, and result tallying.',
    stack: ['Node.js', 'Express.js', 'Solidity', 'Ethereum Sepolia Testnet'],
    demo: 'https://blockchain-voting-tauy.onrender.com/homepage.html',
    repo: 'https://github.com/lesley-ayemi/blockchain-voting'
  }
]

const hostname = (url) => {
  try {
    return new URL(url).hostname + new URL(url).pathname.replace(/\/$/, '')
  } catch {
    return url
  }
}
</script>

<template>
  <section id="projects">
    <div class="container">
      <div class="cmd-header">
        <span class="prompt">$</span>
        <span class="cmd">ls</span>
        <span class="flag">-la projects/</span>
      </div>

      <div class="grid">
        <article v-for="p in projects" :key="p.name" class="file-card card">
          <div class="preview" :class="p.kind">
            <div class="preview-bar">
              <span class="dot dot-red"></span>
              <span class="dot dot-yellow"></span>
              <span class="dot dot-green"></span>
              <span class="preview-url">{{ p.demo ? hostname(p.demo) : 'localhost // no live preview' }}</span>
            </div>
            <div class="preview-body">
              <span class="preview-watermark">{{ p.ext }}</span>
              <span class="preview-tag">{{ p.name }}{{ p.ext }}</span>
            </div>
          </div>

          <div class="file-head">
            <span class="badge">{{ p.ext }}</span>
            <span class="filename">{{ p.name }}{{ p.ext }}</span>
          </div>
          <h3>{{ p.title }}</h3>
          <p class="desc">{{ p.desc }}</p>
          <div class="stack">
            <span v-for="s in p.stack" :key="s" class="tag">{{ s }}</span>
          </div>
          <div class="links">
            <a v-if="p.demo" :href="p.demo" target="_blank" rel="noopener noreferrer" class="btn btn-ghost small">live demo</a>
            <span v-else class="btn btn-ghost small disabled">live demo soon</span>
            <a v-if="p.repo" :href="p.repo" target="_blank" rel="noopener noreferrer" class="btn btn-ghost small">source</a>
            <span v-else class="btn btn-ghost small disabled">source private</span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.file-card {
  padding: 0;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

/* ===== Browser-window style preview mockup ===== */
.preview {
  border-bottom: 1px solid var(--border);
  background: var(--surface-alt);
}

.preview-bar {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 10px 12px;
  border-bottom: 1px solid var(--border);
  background: var(--surface);
}

.dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
.dot-red { background: #e0553f; }
.dot-yellow { background: #c98a3e; }
.dot-green { background: #1f9d74; }

.preview-url {
  margin-left: 8px;
  font-family: var(--font-mono);
  font-size: 0.72rem;
  color: var(--muted);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.preview-body {
  position: relative;
  height: 150px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  background:
    repeating-linear-gradient(135deg, var(--accent) 0, var(--accent) 1px, transparent 1px, transparent 18px);
  background-color: var(--surface-alt);
  background-blend-mode: overlay;
  opacity: 0.9;
}

.preview.function .preview-body {
  background:
    repeating-linear-gradient(135deg, var(--accent-2) 0, var(--accent-2) 1px, transparent 1px, transparent 18px);
  background-color: var(--surface-alt);
  background-blend-mode: overlay;
}

.preview-watermark {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 2.6rem;
  color: var(--text);
  opacity: 0.08;
  letter-spacing: -0.02em;
}

.preview-tag {
  position: absolute;
  bottom: 10px;
  left: 12px;
  font-family: var(--font-mono);
  font-size: 0.72rem;
  padding: 3px 8px;
  border-radius: 5px;
  background: var(--surface);
  border: 1px solid var(--border);
  color: var(--muted);
}

/* ===== Card body ===== */
.file-head,
h3,
.desc,
.stack,
.links {
  padding-left: 22px;
  padding-right: 22px;
}

.file-head {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 18px;
  margin-bottom: 14px;
}
.badge {
  font-family: var(--font-mono);
  font-size: 0.72rem;
  padding: 3px 8px;
  border-radius: 5px;
  background: var(--surface-alt);
  color: var(--accent);
  border: 1px solid var(--border);
}
.filename {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: var(--muted);
}

h3 { font-size: 1.15rem; margin-bottom: 8px; }

.desc { color: var(--muted); font-size: 0.94rem; flex: 1; margin: 0 0 16px; }

.stack { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 18px; }
.tag {
  font-family: var(--font-mono);
  font-size: 0.72rem;
  padding: 4px 8px;
  border-radius: 5px;
  background: var(--surface-alt);
  color: var(--text);
  border: 1px solid var(--border);
}

.links { display: flex; gap: 10px; margin-bottom: 22px; }
.btn.small { padding: 8px 14px; font-size: 0.78rem; }
.btn.disabled {
  opacity: 0.5;
  cursor: default;
  pointer-events: none;
}
</style>
