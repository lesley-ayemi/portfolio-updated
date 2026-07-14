<script setup>
const facts = [
  { label: 'location', value: 'london, UK (open to relocation)' },
  { label: 'focus', value: 'Web platforms, developer tooling' },
  { label: 'experience', value: '6 years professional' },
  // { label: 'currently', value: 'Senior Engineer @ Fictional Co.' }
]
</script>

<template>
  <section id="about">
    <div class="container">
      <div class="cmd-header">
        <span class="prompt">$</span>
        <span class="cmd">whoami</span>
        <span class="flag">--verbose</span>
      </div>

      <div class="about-grid">
        <div class="about-copy">
          <h2>About</h2>
          <p>
            I'm a full-stack engineer, and the part of the job I actually enjoy is the middle ground: where the architecture decisions meet what the user actually experiences day to day. Six years in now, across internal tools, customer-facing platforms, and a couple of products that didn't make it. The failed ones taught me more than the shipped ones, if I'm honest.
          </p>
          <p>
            My stack shifts depending on what the job needs — Vue and React on the frontend, Node, Python, PHP and Laravel on the backend. Dashboards that need to handle real data volume, auth systems, APIs that can't fall over under load. Lately that also means pairing years of hands-on experience with AI tools to move faster, without skipping the part where the architecture actually fits the application it's built for.
          </p>
          <p>
            Outside of work I mentor junior developers with She Code Africa, and I keep a couple of small open-source tools ticking over in my spare time.
          </p>
        </div>

        <dl class="facts card">
          <div v-for="f in facts" :key="f.label" class="fact-row">
            <dt>{{ f.label }}</dt>
            <dd>{{ f.value }}</dd>
          </div>
        </dl>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: 1.4fr 1fr;
  gap: 48px;
}

h2 { font-size: 1.9rem; margin-bottom: 18px; }

.about-copy p { color: var(--muted); margin: 0 0 16px; max-width: 62ch; }

.facts {
  padding: 8px 0;
  height: fit-content;
}
.fact-row {
  display: flex;
  justify-content: space-between;
  gap: 12px;
  padding: 14px 20px;
  border-bottom: 1px solid var(--border);
  font-family: var(--font-mono);
  font-size: 0.85rem;
}
.fact-row:last-child { border-bottom: none; }
dt { color: var(--accent); }
dd { margin: 0; color: var(--text); text-align: right; }

@media (max-width: 860px) {
  .about-grid { grid-template-columns: 1fr; }
}
</style>
