<script lang="ts">
  import { DateTime } from 'luxon'

  export let start: number
  export let end: number = null

  function years(start: number, end?: number): number {
    const endYear = end || Number.parseInt(DateTime.now().toFormat('y'), 10)
    const difference = endYear - start
    return difference
  }
</script>

<div class="text-3xl font-bold">{years(start, end)} years</div>
