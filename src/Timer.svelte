<script lang="ts">
  import { onDestroy } from 'svelte';
  export let endDate: number = 0;
  let current = Date.now();
  let frame;
  function formatDuration(ms: number) {
    if (ms <= 0) {
      if (frame) {
        cancelAnimationFrame(frame);
      }
      return '0d 00:00:00';
    }
    const secs = Math.floor(ms / 1000);
    const mins = Math.floor(secs / 60);
    const srem = Math.floor(secs % 60);
    const hour = Math.floor(mins / 60);
    const mrem = Math.floor(mins % 60);
    const days = Math.floor(hour / 24);
    const hrem = Math.floor(hour % 24);
    return `${days}d ${hrem < 10 ? '0' : ''}${hrem}:${mrem < 10 ? '0' : ''}${mrem}:${srem < 10 ? '0' : ''}${srem}`;
  }
  $: timeStr = formatDuration(endDate - current);
  function countdown() {
    frame = requestAnimationFrame(countdown);
    current = Date.now();
  }
  onDestroy(() => cancelAnimationFrame(frame));
  countdown();
</script>
<div class="font-mono">
{timeStr}
</div>
