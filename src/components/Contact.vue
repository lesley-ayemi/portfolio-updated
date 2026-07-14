<script setup>
import { ref } from 'vue'

const email = 'leeayemi@gmail.com'
const githubUrl = 'https://github.com/lesley-ayemi'
const githubLabel = 'github.com/lesley-ayemi'
const linkedinUrl = 'https://linkedin.com/in/lesleyayemi'
const linkedinLabel = 'linkedin.com/in/lesleyayemi'

const copied = ref(false)
let resetTimer = null

async function copyEmail() {
  try {
    await navigator.clipboard.writeText(email)
  } catch {
    // clipboard API unavailable — the mailto link below still works
  }
  copied.value = true
  clearTimeout(resetTimer)
  resetTimer = setTimeout(() => { copied.value = false }, 1800)
}
</script>

<template>
  <section id="contact">
    <div class="container">
      <div class="cmd-header">
        <span class="prompt">$</span>
        <span class="cmd">cat</span>
        <span class="flag">contact.md</span>
      </div>

      <div class="contact-grid">
        <div class="contact-copy">
          <p class="status">
            <span class="dot"></span>
            available for opportunities
          </p>
          <h2>
            Let's build<br />
            <span class="accent-italic">something great.</span>
          </h2>
          <p class="lede">
            Have a role, project, or idea worth discussing? Reach out directly —
            I reply within a couple of days.
          </p>

          <div class="icon-row">
            <a class="icon-btn" :href="`mailto:${email}`" title="Email me" aria-label="Email me">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16v16H4z"/><path d="m4 6 8 7 8-7"/></svg>
            </a>
            <a class="icon-btn" :href="githubUrl" target="_blank" rel="noopener" title="GitHub" aria-label="GitHub">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.48 2 2 6.58 2 12.25c0 4.53 2.87 8.37 6.84 9.73.5.1.68-.22.68-.49v-1.9c-2.78.62-3.37-1.21-3.37-1.21-.46-1.19-1.11-1.5-1.11-1.5-.91-.64.07-.63.07-.63 1 .07 1.53 1.05 1.53 1.05.9 1.57 2.36 1.12 2.93.85.09-.67.35-1.12.64-1.38-2.22-.26-4.56-1.13-4.56-5.03 0-1.11.39-2.02 1.03-2.73-.1-.26-.45-1.3.1-2.7 0 0 .84-.27 2.75 1.05a9.3 9.3 0 015 0c1.9-1.32 2.75-1.05 2.75-1.05.55 1.4.2 2.44.1 2.7.64.71 1.03 1.62 1.03 2.73 0 3.91-2.34 4.77-4.57 5.02.36.32.68.94.68 1.9v2.82c0 .27.18.6.69.49A10.26 10.26 0 0022 12.25C22 6.58 17.52 2 12 2z"/></svg>
            </a>
            <a class="icon-btn" :href="linkedinUrl" target="_blank" rel="noopener" title="LinkedIn" aria-label="LinkedIn">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M4.98 3.5C4.98 4.88 3.88 6 2.5 6S0 4.88 0 3.5 1.12 1 2.5 1s2.48 1.12 2.48 2.5zM.24 8.25h4.5V23H.24V8.25zM8.5 8.25h4.32v2.02h.06c.6-1.14 2.07-2.34 4.26-2.34 4.56 0 5.4 3 5.4 6.9V23h-4.5v-6.98c0-1.66-.03-3.8-2.32-3.8-2.32 0-2.68 1.81-2.68 3.68V23H8.5V8.25z"/></svg>
            </a>
          </div>
        </div>

        <div class="term card" aria-hidden="true">
          <div class="window-bar">
            <span class="wdot" style="--c:#f2705a"></span>
            <span class="wdot" style="--c:#f2c14e"></span>
            <span class="wdot" style="--c:#3fbf8f"></span>
            <span class="wfile">contact.sh</span>
          </div>
          <div class="term-body">
            <p class="line"><span class="p">$</span> <span class="kw">whoami</span></p>
            <p class="line dim">lesley ayemi · full-stack engineer</p>

            <p class="line"><span class="p">$</span> <span class="kw">contact</span> --list</p>

            <div class="rows">
              <div class="row">
                <span class="key">email</span>
                <a class="val link" :href="`mailto:${email}`">{{ email }}</a>
                <button class="copy" type="button" @click="copyEmail" :title="copied ? 'copied!' : 'copy'">
                  <svg v-if="!copied" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="12" height="12" rx="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg>
                  <svg v-else width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6 9 17l-5-5"/></svg>
                </button>
              </div>
              <div class="row">
                <span class="key">github</span>
                <a class="val link" :href="githubUrl" target="_blank" rel="noopener">{{ githubLabel }}</a>
              </div>
              <div class="row">
                <span class="key">linkedin</span>
                <a class="val link" :href="linkedinUrl" target="_blank" rel="noopener">{{ linkedinLabel }}</a>
              </div>
            </div>

            <p class="line"><span class="p">$</span> <span class="kw">echo</span> $STATUS</p>
            <p class="line ok">open to freelance &amp; full-time roles</p>
          </div>
          <p class="compiled"><span class="arrow">&rarr;</span> Ready when you are</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.15fr;
  gap: 64px;
  align-items: center;
}

.contact-copy { min-width: 0; }

.status {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: var(--font-mono);
  font-size: 0.78rem;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: var(--muted);
  margin: 0 0 22px;
}
.dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--success);
  box-shadow: 0 0 0 0 color-mix(in srgb, var(--success) 60%, transparent);
  animation: pulse 2s infinite;
}
@keyframes pulse {
  0% { box-shadow: 0 0 0 0 color-mix(in srgb, var(--success) 45%, transparent); }
  70% { box-shadow: 0 0 0 7px transparent; }
  100% { box-shadow: 0 0 0 0 transparent; }
}

h2 {
  font-family: var(--font-display);
  font-size: clamp(2.1rem, 4vw, 2.9rem);
  line-height: 1.08;
  font-weight: 500;
  margin: 0 0 20px;
}
.accent-italic {
  font-style: italic;
  font-weight: 400;
  color: var(--muted);
}

.lede {
  color: var(--muted);
  max-width: 42ch;
  margin: 0 0 28px;
}

.icon-row {
  display: flex;
  gap: 12px;
}
.icon-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 42px;
  height: 42px;
  border-radius: 50%;
  border: 1px solid var(--border);
  color: var(--text);
  transition: transform 0.15s ease, border-color 0.15s ease, color 0.15s ease;
}
.icon-btn:hover {
  border-color: var(--accent);
  color: var(--accent);
  transform: translateY(-2px);
}

/* ===== Terminal card ===== */
.term {
  overflow: hidden;
  min-width: 0;
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

.term-body {
  margin: 0;
  padding: 22px 20px 6px;
  font-family: var(--font-mono);
  font-size: 0.82rem;
  line-height: 1.7;
}
.line { margin: 0; }
.line.dim { color: var(--muted); margin-bottom: 14px; }
.line.ok { color: var(--success); }
.p { color: var(--accent-2); }
.kw { color: var(--accent); font-weight: 600; }

.rows {
  margin: 8px 0 16px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.row {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 4px 0;
}
.key {
  color: var(--muted);
  width: 76px;
  flex-shrink: 0;
}
.val.link {
  color: var(--text);
  text-decoration: none;
  border-bottom: 1px dashed var(--border);
  word-break: break-all;
}
.val.link:hover { color: var(--accent); border-color: var(--accent); }

.copy {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 26px;
  height: 26px;
  margin-left: 8px;
  border-radius: 6px;
  border: 1px solid transparent;
  background: transparent;
  color: var(--muted);
  cursor: pointer;
  flex-shrink: 0;
}
.copy:hover { border-color: var(--border); color: var(--accent); }

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
  .contact-grid { grid-template-columns: 1fr; }
}
</style>
