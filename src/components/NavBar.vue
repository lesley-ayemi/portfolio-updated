<script setup>
import { ref } from 'vue'
import { useTheme } from '../composables/useTheme.js'

const { theme, toggleTheme } = useTheme()
const open = ref(false)

const links = [
  { href: '#about', label: 'about' },
  { href: '#skills', label: 'skills' },
  { href: '#experience', label: 'experience' },
  { href: '#projects', label: 'projects' },
  { href: '#contact', label: 'contact' }
]

function closeMenu() { open.value = false }
</script>

<template>
  <header class="nav">
    <div class="container nav-inner">
      <a href="#top" class="logo">
        <span class="logo-bracket">&lt;</span>lesley.ayemi<span class="logo-bracket">/&gt;</span>
      </a>

      <nav class="links" :class="{ open }">
        <a v-for="link in links" :key="link.href" :href="link.href" @click="closeMenu">
          <span class="dot">$</span>{{ link.label }}
        </a>
      </nav>

      <div class="actions">
        <button class="theme-toggle" @click="toggleTheme" :aria-label="`Switch to ${theme === 'dark' ? 'light' : 'dark'} mode`">
          <svg v-if="theme === 'dark'" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="12" cy="12" r="4.5" />
            <path d="M12 2v2.5M12 19.5V22M4.2 4.2l1.8 1.8M18 18l1.8 1.8M2 12h2.5M19.5 12H22M4.2 19.8L6 18M18 6l1.8-1.8" />
          </svg>
          <svg v-else width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M21 12.8A9 9 0 1111.2 3a7.2 7.2 0 009.8 9.8z" />
          </svg>
        </button>
        <button class="burger" @click="open = !open" aria-label="Toggle menu">
          <span></span><span></span><span></span>
        </button>
      </div>
    </div>
  </header>
</template>

<style scoped>
.nav {
  position: sticky;
  top: 0;
  z-index: 50;
  background: color-mix(in srgb, var(--bg) 88%, transparent);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid var(--border);
}

.nav-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 16px;
  padding-bottom: 16px;
}

.logo {
  font-family: var(--font-mono);
  font-weight: 600;
  text-decoration: none;
  color: var(--text);
  font-size: 1rem;
}
.logo-bracket { color: var(--accent); }

.links {
  display: flex;
  gap: 24px;
}
.links a {
  font-family: var(--font-mono);
  font-size: 0.88rem;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.15s ease;
}
.links a:hover { color: var(--text); }
.links .dot { color: var(--success); margin-right: 2px; }

.actions { display: flex; align-items: center; gap: 8px; }

.theme-toggle {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  border-radius: var(--radius);
  border: 1px solid var(--border);
  background: var(--surface);
  color: var(--text);
  cursor: pointer;
}
.theme-toggle:hover { border-color: var(--accent); color: var(--accent); }

.burger {
  display: none;
  flex-direction: column;
  gap: 4px;
  width: 36px;
  height: 36px;
  border-radius: var(--radius);
  border: 1px solid var(--border);
  background: var(--surface);
  cursor: pointer;
  align-items: center;
  justify-content: center;
}
.burger span {
  width: 16px;
  height: 2px;
  background: var(--text);
}

@media (max-width: 720px) {
  .links {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: var(--bg);
    border-bottom: 1px solid var(--border);
    flex-direction: column;
    padding: 16px 24px;
    display: none;
  }
  .links.open { display: flex; }
  .burger { display: flex; }
}
</style>
