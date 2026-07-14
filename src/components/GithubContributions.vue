<script setup>
import { ref, computed, onMounted } from 'vue'

const props = defineProps({
  username: { type: String, default: 'octocat' }
})

const days = ref([])
const status = ref('loading') // loading | ready | error

const monthNames = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']

onMounted(async () => {
  try {
    // Public, unofficial GitHub contributions API — no auth required.
    // Swap for your own backend proxy if you need something more guaranteed/stable in production.
    const res = await fetch(`https://github-contributions-api.jogruber.de/v4/${props.username}?y=last`)
    if (!res.ok) throw new Error('request failed')
    const data = await res.json()
    days.value = data.contributions || []
    status.value = 'ready'
  } catch (e) {
    status.value = 'error'
  }
})

const weeks = computed(() => {
  if (!days.value.length) return []
  const result = []
  let currentWeek = []
  const firstDay = new Date(days.value[0].date)
  const startPad = firstDay.getDay() // 0 = Sunday
  for (let i = 0; i < startPad; i++) currentWeek.push(null)

  for (const day of days.value) {
    currentWeek.push(day)
    if (currentWeek.length === 7) {
      result.push(currentWeek)
      currentWeek = []
    }
  }
  if (currentWeek.length) {
    while (currentWeek.length < 7) currentWeek.push(null)
    result.push(currentWeek)
  }
  return result
})

const monthLabels = computed(() => {
  const labels = []
  let lastMonth = null
  weeks.value.forEach((week, i) => {
    const firstReal = week.find((d) => d)
    if (!firstReal) return
    const month = new Date(firstReal.date).getMonth()
    if (month !== lastMonth) {
      labels.push({ column: i + 1, label: monthNames[month] })
      lastMonth = month
    }
  })
  return labels
})

const totalContributions = computed(() =>
  days.value.reduce((sum, d) => sum + (d?.count || 0), 0)
)
</script>

<template>
  <div class="contrib">
    <div class="contrib-head">
      <span class="label">Recent Contributions</span>
      <a :href="`https://github.com/${username}`" target="_blank" rel="noopener" class="handle">
        @{{ username }}
      </a>
    </div>

    <div v-if="status === 'loading'" class="state">loading contribution history…</div>
    <div v-else-if="status === 'error'" class="state">
      couldn't load live data — check the username or try again later.
    </div>

    <template v-else>
      <div class="grid-wrap">
        <div class="months" :style="{ gridTemplateColumns: `repeat(${weeks.length}, 1fr)` }">
          <span
            v-for="m in monthLabels"
            :key="m.column + m.label"
            class="month"
            :style="{ gridColumnStart: m.column }"
          >{{ m.label }}</span>
        </div>

        <div class="grid" :style="{ gridTemplateColumns: `repeat(${weeks.length}, 1fr)` }">
          <div v-for="(week, wi) in weeks" :key="wi" class="col">
            <span
              v-for="(day, di) in week"
              :key="di"
              class="cell"
              :class="day ? `level-${day.level}` : 'empty'"
              :title="day ? `${day.count} contributions on ${day.date}` : ''"
            ></span>
          </div>
        </div>
      </div>

      <div class="legend">
        <span class="total">{{ totalContributions.toLocaleString() }} contributions</span>
        <span class="scale">
          Less
          <i class="cell level-0"></i>
          <i class="cell level-1"></i>
          <i class="cell level-2"></i>
          <i class="cell level-3"></i>
          <i class="cell level-4"></i>
          More
        </span>
      </div>
    </template>
  </div>
</template>

<style scoped>
.contrib {
  margin-top: 28px;
  max-width: 100%;
}

.contrib-head {
  display: flex;
  align-items: baseline;
  gap: 10px;
  margin-bottom: 12px;
  font-family: var(--font-mono);
  font-size: 0.82rem;
}
.label { color: var(--text); font-weight: 600; }
.handle { color: var(--accent); text-decoration: none; }
.handle:hover { text-decoration: underline; }

.state {
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: var(--muted);
}

.grid-wrap {
  overflow-x: auto;
  padding-bottom: 4px;
}

.months {
  display: grid;
  gap: 3px;
  margin-bottom: 4px;
  min-width: 480px;
}
.month {
  font-family: var(--font-mono);
  font-size: 0.68rem;
  color: var(--muted);
}

.grid {
  display: grid;
  gap: 3px;
  min-width: 480px;
}
.col {
  display: grid;
  grid-template-rows: repeat(7, 1fr);
  gap: 3px;
}

.cell {
  width: 100%;
  aspect-ratio: 1;
  min-width: 10px;
  min-height: 10px;
  border-radius: 2px;
  background: var(--border);
  display: inline-block;
}
.cell.empty { background: transparent; }
.cell.level-0 { background: var(--surface-alt); border: 1px solid var(--border); }
.cell.level-1 { background: color-mix(in srgb, var(--success) 30%, var(--surface-alt)); }
.cell.level-2 { background: color-mix(in srgb, var(--success) 55%, var(--surface-alt)); }
.cell.level-3 { background: color-mix(in srgb, var(--success) 80%, var(--surface-alt)); }
.cell.level-4 { background: var(--success); }

.legend {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 10px;
  font-family: var(--font-mono);
  font-size: 0.72rem;
  color: var(--muted);
  flex-wrap: wrap;
  gap: 8px;
}
.scale {
  display: flex;
  align-items: center;
  gap: 3px;
}
.scale .cell {
  width: 10px;
  height: 10px;
  min-width: 10px;
  min-height: 10px;
  margin: 0 1px;
}
</style>
