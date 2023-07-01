<script lang="ts">
  import { onMount } from 'svelte'
  import AnalogClock from './lib/AnalogClock.svelte'
  import DigitalClock from './lib/DigitalClock.svelte'

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

<main class="p-8 max-w-4xl mx-auto h-screen flex flex-col md:flex-row items-center gap-20 pt-20 md:pt-0">
  <AnalogClock {date} />
  <DigitalClock {date} />
</main>
