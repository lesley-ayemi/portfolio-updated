<script setup>
const groups = [
  {
    label: 'languages',
    kind: 'string',
    items: ['JavaScript', 'TypeScript', 'Python', 'PHP', 'SQL', 'C#', 'Dart', 'Solidity']
  },
  {
    label: 'web & frontend',
    kind: 'keyword',
    items: ['React.js', 'Next.js', 'Redux', 'Tailwind CSS', 'Sass', 'WordPress']
  },
  {
    label: 'backend & apis',
    kind: 'function',
    items: ['Node.js', 'Express.js', 'Django', 'Laravel', 'REST APIs']
  },
  {
    label: 'mobile',
    kind: 'string',
    items: ['Flutter', 'React Native', 'Swift (iOS)', 'Kotlin (Android)']
  },
  {
    label: 'databases & cloud',
    kind: 'number',
    items: ['MongoDB', 'MySQL', 'PostgreSQL', 'DynamoDB', 'Firebase', 'SQL Server', 'Redis', 'AWS', 'GCP']
  },
  {
    label: 'it support & systems',
    kind: 'keyword',
    items: ['Windows', 'macOS', 'Linux', 'Active Directory', 'Microsoft Intune', 'Jamf', 'Apple Business Manager', 'Microsoft 365', 'PowerShell', 'DNS/IP/VPN Troubleshooting', 'Asset Management']
  },
  {
    label: 'tools & methods',
    kind: 'comment',
    items: ['Git', 'GitHub', 'GitLab', 'Bitbucket', 'Jira', 'Trello', 'Agile/Scrum', 'TDD', 'BDD']
  }
]
</script>

<template>
  <section id="skills">
    <div class="container">
      <div class="cmd-header">
        <span class="prompt">$</span>
        <span class="cmd">ls</span>
        <span class="flag">skills/ --tree</span>
      </div>

      <h2 class="visually-hidden">Skills</h2>

      <div class="skill-groups">
        <div class="skill-group card" v-for="g in groups" :key="g.label">
          <p class="group-label"># {{ g.label }}</p>
          <div class="chips">
            <span v-for="item in g.items" :key="item" class="chip" :class="g.kind">{{ item }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.visually-hidden {
  position: absolute;
  width: 1px; height: 1px;
  overflow: hidden;
  clip: rect(0 0 0 0);
}

.skill-groups {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
  gap: 18px;
}

.skill-group { padding: 20px; }

.group-label {
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: var(--muted);
  margin: 0 0 14px;
}

.chips { display: flex; flex-wrap: wrap; gap: 8px; }

.chip {
  font-family: var(--font-mono);
  font-size: 0.82rem;
  padding: 6px 10px;
  border-radius: 6px;
  border: 1px solid var(--border);
  background: var(--surface-alt);
}

/* syntax-highlight inspired colour coding, muted for readability in both themes */
.chip.string   { color: var(--success); border-color: color-mix(in srgb, var(--success) 40%, var(--border)); }
.chip.keyword  { color: var(--accent);  border-color: color-mix(in srgb, var(--accent) 40%, var(--border)); }
.chip.function { color: var(--accent-2); border-color: color-mix(in srgb, var(--accent-2) 40%, var(--border)); }
.chip.number   { color: #c98a3e; border-color: color-mix(in srgb, #c98a3e 40%, var(--border)); }
.chip.comment  { color: var(--muted); font-style: italic; }
</style>
