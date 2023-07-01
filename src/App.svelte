<script lang="ts">
  import { onMount } from 'svelte'
  import AnalogClock from './lib/AnalogClock.svelte'

  let date: Date = new Date()

  onMount(() => {
    const interval = setInterval(() => {
      date = new Date()
    }, 100)
    return () => {
      clearInterval(interval)
    }
  })
</script>

<main class="p-6">
  <AnalogClock {date} />
</main>
