<script setup>
const year = new Date().getFullYear()
</script>

<template>
  <footer class="footer">
    <div class="container footer-inner">
      <p class="cmdline"><span class="prompt">$</span> echo "thanks for stopping by"</p>
      <p class="meta">&copy; {{ year }} lesley ayemi. Built with Vue &amp; Node.js.</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  border-top: 1px solid var(--border);
  padding: 32px 0;
}
.footer-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
}
.cmdline {
  font-family: var(--font-mono);
  font-size: 0.85rem;
  margin: 0;
  color: var(--muted);
}
.prompt { color: var(--success); margin-right: 6px; }
.meta {
  margin: 0;
  font-size: 0.82rem;
  color: var(--muted);
}
</style>
