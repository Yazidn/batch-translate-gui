<script>
    export let isRunning;
</script>

{#if isRunning}
    <div class="anim text-white absolute top-0 left-0 right-0 bottom-0 bg-blue-600 flex items-center justify-center">
        Loading..
    </div>
{/if}