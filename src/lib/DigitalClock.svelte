<script lang="ts">
  export let date: Date

  import { format } from 'date-fns'
</script>

<div class="text-center">
  <p class="text-8xl font-bold font-mono">
    {format(date, 'hh:mm')}<span class="text-5xl">{format(date, ':ss')}</span>
  </p>
  <p class="mt-2 text-4xl font-bold font-mono">
  {format(date, 'yyyy.MM.dd EEE')}
  </p>
</div>
