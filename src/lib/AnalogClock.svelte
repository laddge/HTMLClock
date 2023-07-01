<script lang="ts">
  export let date: Date

  $: hDeg = 360 / 720 * ((date.getHours() % 12) * 60 + date.getMinutes())  // 360deg / 720min * {min of 12h}
  $: mDeg = 360 / 3600 * (date.getMinutes() * 60 + Math.floor(date.getSeconds() / 20) * 20)  // 360deg / 3600sec * {sec (20sec step) of 1h}
  $: sDeg = 360 / 60 * date.getSeconds()  // 360deg / 60sec * {sec}
</script>

<div class="relative aspect-square w-full max-w-lg mx-auto overflow-hidden">
  {#each {length: 60} as _, d}
    <div class="w-full h-full absolute 0" style={`transform: rotate(${d * 6}deg);`}>
      {#if d % 5 == 0}
      <div class="w-[calc(50%+2px)] h-5 border-r-4 border-current" />
      {:else}
      <div class="w-[calc(50%+1px)] h-1 border-r-2 border-current" />
      {/if}
    </div>
  {/each}
  <div class="w-2/3 h-2/3 absolute top-[calc(100%/6)] left-[calc(100%/6)]" style={`transform: rotate(${hDeg}deg);`}>
    <div class="w-[calc(50%+4px)] h-1/2 border-r-8 border-current" />
  </div>
  <div class="w-full h-full absolute top-0" style={`transform: rotate(${mDeg}deg);`}>
    <div class="w-[calc(50%+2px)] h-1/2 border-r-4 border-current" />
  </div>
  <div class="w-full h-full absolute top-0" style={`transform: rotate(${sDeg}deg);`}>
    <div class="w-[calc(50%+1px)] h-1/2 border-r-2 border-error" />
  </div>
</div>
