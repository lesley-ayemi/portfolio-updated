<script setup>
import { ref } from 'vue'

const initialCount = 4
const expanded = ref(false)

const roles = [
  {
    hash: 'a3f9c1e',
    role: 'AI / Machine Learning Product Contributor',
    company: 'Alignerr',
    period: 'Nov 2025 — Present',
    points: [
      'Annotate real-world programming tasks in live Code Bench environments for AI model alignment.',
      'Contribute to Code Reinforcement Learning (Code RL) and Greenfield Vibe coding annotation projects across multiple AI models.'
    ]
  },
  {
    hash: '5b8f0d2',
    role: 'Co-Founder & Full-Stack Developer',
    company: 'Softalx Solutions',
    period: 'May 2020 — Present',
    points: [
      'Co-founded a software solutions company delivering web applications and digital services, selecting the right technologies per project rather than a fixed stack.',
      'Own projects end-to-end, from client requirements and technical design through development, deployment, and ongoing support.',
      'Led Agile delivery across cross-functional teams of 8–12, improving sprint efficiency by 30% and on-time delivery of milestones by 25%.'
    ]
  },
  {
    hash: '7e21bda',
    role: 'Customer Assistant',
    company: 'Marks & Spencer',
    period: 'Nov 2025 — Jul 2026',
    points: [
      'Coordinated nightly goods-in across ambient and cold-chain deliveries, ensuring compliance before shop-floor release.',
      'Ran defect/waste control and maintained traceability via tagging and ticketing.',
      'Provided escalation support during short staffing to protect delivery timelines and service continuity.'
    ]
  },
  {
    hash: 'c58d2f6',
    role: 'Software Development & IT Support Intern',
    company: 'Bluebow Research Consultancy',
    period: 'Nov 2024 — Aug 2025',
    points: [
      'Integrated 5+ third-party APIs, reducing development effort by 20%.',
      'Shipped features that lifted app engagement by 25% and improved load speed/responsiveness by 15%.',
      'Resolved 20+ support tickets weekly across Windows, macOS, VPN, printer, and account-access issues, managing endpoint enrolment via Microsoft Intune, Jamf, and Apple Business Manager.',
      'Authored 10+ technical docs, cutting developer onboarding time by 30%.'
    ]
  },
  {
    hash: '91ab4d0',
    role: 'Software Engineer (Remote)',
    company: 'Seed Credit',
    period: 'Nov 2024 — Jul 2025',
    points: [
      'Refactored backend with SQL indexing and async job queues, cutting transaction processing speed by 40%.',
      'Integrated Flutterwave and Paystack payment gateways, lifting checkout success by 30% and reducing cart abandonment.',
      'Collaborated in weekly code reviews and paired programming sessions, contributing to a 25% reduction in sprint delivery time.'
    ]
  },
  {
    hash: 'e34a7c9',
    role: 'Freelance Software Developer',
    company: 'Upwork',
    period: 'Dec 2020 — Aug 2024',
    points: [
      'Delivered 10+ client projects spanning web and mobile applications, API development, and cloud integrations (AWS, GCP), maintaining a track record of repeat engagements.',
      'Gained hands-on experience integrating AI tooling (OpenAI API, LangChain) into client products.'
    ]
  },
  {
    hash: '2f7e6a3',
    role: 'Junior Web Developer',
    company: 'APTECH Computer Education',
    period: 'Jan 2022 — Nov 2022',
    points: [
      'Delivered 10+ school portals, e-learning sites, and management systems using PHP (Laravel), MySQL, and SQL Server, alongside Python desktop utilities.',
      'Built systems that streamlined student registration, reporting, and attendance tracking across multiple schools, reducing manual administrative work.',
      'Mentored junior students in web development fundamentals and database design, supporting their progression through practical projects.'
    ]
  },
  {
    hash: 'b16f9a4',
    role: 'Information Technology Support Analyst',
    company: 'Coriftech Solutions',
    period: 'May 2021 — Dec 2021',
    points: [
      'Delivered remote IT support for distributed teams, resolving software and account-access issues.',
      'Managed onboarding processes, including account setup and permissions administration.',
      'Troubleshot system and platform issues, escalating and collaborating cross-functionally on complex cases through to resolution.'
    ]
  },
  {
    hash: 'd049b1c',
    role: 'Learning Facilitator',
    company: 'Coriftech Solutions',
    period: 'Nov 2020 — May 2021',
    points: [
      'Trained working professionals in front-end development (HTML5, CSS3, JavaScript), with 80%+ going on to independently build responsive, mobile-friendly websites.',
      'Introduced back-end fundamentals using PHP and MySQL, enabling learners to build simple dynamic applications.',
      'Delivered hands-on WordPress CMS training, helping 90% of trainees launch and manage their own websites.'
    ]
  },
  {
    hash: '6a1c8e2',
    role: 'Quality Manual Tester',
    company: 'Hulkma.com',
    period: 'May 2020 — Nov 2020',
    points: [
      'Executed 30+ test cases and logged 50+ bugs via Jira/Bugzilla, cutting issue turnaround time by 20%.',
      'Tested across 5+ browsers/devices, improving cross-platform compatibility by over 90%.'
    ]
  }
]
</script>

<template>
  <section id="experience">
    <div class="container">
      <div class="cmd-header">
        <span class="prompt">$</span>
        <span class="cmd">git log</span>
        <span class="flag">--oneline --graph experience</span>
      </div>

      <ol class="timeline" :class="{ 'is-expanded': expanded }">
        <li
          v-for="(r, i) in roles"
          :key="r.hash"
          class="entry"
          :class="{ 'is-extra': i >= initialCount }"
        >
          <div class="rail">
            <span class="node"></span>
            <span class="line"></span>
          </div>
          <div class="entry-body card">
            <p class="commit-line">
              <span class="hash">{{ r.hash }}</span>
              <span class="role">{{ r.role }}</span>
              <span class="at">@ {{ r.company }}</span>
            </p>
            <p class="period">{{ r.period }}</p>
            <ul>
              <li v-for="p in r.points" :key="p">{{ p }}</li>
            </ul>
          </div>
        </li>
      </ol>

      <button v-if="!expanded" type="button" class="load-more btn btn-ghost" @click="expanded = true">
        load more <span class="count">(+{{ roles.length - initialCount }})</span>
      </button>
    </div>
  </section>
</template>

<style scoped>
.timeline {
  list-style: none;
  margin: 0;
  padding: 0;
}

.entry {
  display: grid;
  grid-template-columns: 28px 1fr;
  gap: 20px;
}

.rail {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.node {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: var(--accent);
  margin-top: 26px;
  flex-shrink: 0;
}
.line {
  flex: 1;
  width: 2px;
  background: var(--border);
}
.entry:last-child .line { display: none; }

.entry-body {
  padding: 22px 24px;
  margin-bottom: 24px;
}

.commit-line {
  font-family: var(--font-mono);
  font-size: 0.95rem;
  margin: 0 0 4px;
}
.hash { color: var(--accent-2); margin-right: 10px; }
.role { font-weight: 600; }
.at { color: var(--muted); margin-left: 6px; }

.period {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: var(--muted);
  margin: 0 0 14px;
}

ul { margin: 0; padding-left: 20px; color: var(--muted); }
li { margin-bottom: 6px; }

.load-more {
  display: none;
  width: 100%;
  justify-content: center;
  font-size: 0.85rem;
}
.load-more .count { color: var(--muted); margin-left: 4px; }

@media (max-width: 720px) {
  .entry.is-extra { display: none; }
  .timeline.is-expanded .entry.is-extra { display: grid; }
  .timeline:not(.is-expanded) .entry:nth-child(4) .line { display: none; }

  .load-more { display: flex; }
}
</style>
