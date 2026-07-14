<script setup>
import GithubContributions from './GithubContributions.vue'

// Swap this for your own GitHub username.
const githubUsername = 'lesley-ayemi'
</script>

<template>
  <section id="top" class="hero">
    <div class="container hero-grid">
      <div class="hero-copy">
        <p class="eyebrow-line">Portfolio 2026</p>

        <h1 class="headline">
          <span class="first">lesley</span>
          <span class="last">ayemi</span>
        </h1>

        <p class="role">IT Support & Software Engineer</p>
        <p class="credential">BSc Information Technology Graduate</p>
        <p class="lede">
          Building robust web software. Specializing in Vue, Node.js, and pragmatic system design.
        </p>

        <div class="hero-actions">
          <a class="btn btn-primary" href="#projects">View Work</a>
          <a class="btn btn-ghost" href="#contact">Get in Touch</a>
          <a class="btn btn-ghost" :href="`https://github.com/${githubUsername}`" target="_blank" rel="noopener">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.48 2 2 6.58 2 12.25c0 4.53 2.87 8.37 6.84 9.73.5.1.68-.22.68-.49v-1.9c-2.78.62-3.37-1.21-3.37-1.21-.46-1.19-1.11-1.5-1.11-1.5-.91-.64.07-.63.07-.63 1 .07 1.53 1.05 1.53 1.05.9 1.57 2.36 1.12 2.93.85.09-.67.35-1.12.64-1.38-2.22-.26-4.56-1.13-4.56-5.03 0-1.11.39-2.02 1.03-2.73-.1-.26-.45-1.3.1-2.7 0 0 .84-.27 2.75 1.05a9.3 9.3 0 015 0c1.9-1.32 2.75-1.05 2.75-1.05.55 1.4.2 2.44.1 2.7.64.71 1.03 1.62 1.03 2.73 0 3.91-2.34 4.77-4.57 5.02.36.32.68.94.68 1.9v2.82c0 .27.18.6.69.49A10.26 10.26 0 0022 12.25C22 6.58 17.52 2 12 2z"/></svg>
            GitHub
          </a>
        </div>

        <GithubContributions :username="githubUsername" />
      </div>

      <div class="code-window card" aria-hidden="true">
        <div class="window-bar">
          <span class="wdot" style="--c:#f2705a"></span>
          <span class="wdot" style="--c:#f2c14e"></span>
          <span class="wdot" style="--c:#3fbf8f"></span>
          <span class="wfile">Profile.tsx</span>
        </div>
        <pre class="code"><code><span class="cm">// Defined engineer profile</span>

<span class="kw">import</span> React, { useState } <span class="kw">from</span> <span class="str">'react'</span>;
<span class="kw">const</span> <span class="fn">lesleyProfile</span> = () <span class="ar">=&gt;</span> {

  <span class="kw">const</span> [status] = <span class="fn">useState</span>(
    <span class="str">'Full-Stack Software Engineer'</span>
  );

  <span class="kw">return</span> (
    <span class="tag">&lt;Engineer</span>
      <span class="attr">name</span>=<span class="str">"lesley ayemi"</span>
      <span class="attr">focus</span>=<span class="str">"Vue, Node, systems design"</span>
      <span class="attr">languages</span>={[<span class="str">'JavaScript'</span>, <span class="str">'TypeScript'</span>, <span class="str">'Python'</span>,<span class="str">'PHP'</span>]}
      <span class="attr">status</span>={status}
    <span class="tag">/&gt;</span>
  );
};</code></pre>
        <p class="compiled"><span class="arrow">&rarr;</span> Compiled successfully</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero { padding-top: 72px; }

.hero-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: start;
}

.hero-copy,
.code-window {
  min-width: 0;
}

.eyebrow-line {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--muted);
  padding-bottom: 10px;
  border-bottom: 1px solid var(--border);
  display: inline-block;
  margin: 0 0 28px;
}

.headline {
  font-family: var(--font-display);
  line-height: 0.98;
  margin: 0 0 22px;
}
.headline .first {
  display: block;
  font-size: clamp(3rem, 6.2vw, 4.6rem);
  font-weight: 500;
  color: var(--text);
}
.headline .last {
  display: block;
  font-size: clamp(3rem, 6.2vw, 4.6rem);
  font-weight: 400;
  font-style: italic;
  color: var(--muted);
}

.role {
  font-size: 1.3rem;
  font-weight: 600;
  margin: 0 0 6px;
}
.credential {
  color: var(--muted);
  font-size: 0.95rem;
  margin: 0 0 16px;
}
.lede {
  color: var(--muted);
  max-width: 42ch;
  margin: 0 0 30px;
}

.hero-actions {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 8px;
}
.btn-primary { background: var(--text); color: var(--bg); }
.btn-primary:hover { background: var(--accent); }

/* ===== Code window ===== */
.code-window {
  overflow: hidden;
  position: sticky;
  top: 96px;
}
.window-bar {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px 16px;
  border-bottom: 1px solid var(--border);
  background: var(--surface-alt);
}
.wdot { width: 11px; height: 11px; border-radius: 50%; background: var(--c); }
.wfile {
  margin-left: 10px;
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: var(--muted);
}

.code {
  margin: 0;
  padding: 22px 20px;
  font-family: var(--font-mono);
  font-size: 0.82rem;
  line-height: 1.7;
  white-space: pre-wrap;
  word-break: break-word;
}
.cm { color: var(--muted); font-style: italic; }
.kw { color: var(--accent-2); font-weight: 600; }
.fn { color: var(--accent); }
.str { color: var(--success); }
.tag { color: #d1538a; }
.attr { color: #c98a3e; }
.ar { color: var(--text); }

.compiled {
  margin: 0;
  padding: 12px 20px 18px;
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: var(--success);
  border-top: 1px dashed var(--border);
}
.arrow { margin-right: 6px; }

@media (max-width: 900px) {
  .hero-grid { grid-template-columns: 1fr; }
  .code-window { position: static; }
}
</style>
