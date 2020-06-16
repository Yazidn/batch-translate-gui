<script>
    import Translation from './translation.svelte';

    export let translations = [];
    export let supportedLanguages = [];
</script>

<main class="pt-16">
    <div class="cards p-2">
        {#each translations as translation, index}
            <Translation text={translation.text} lang={translation.lang} language={supportedLanguages[index].name}/>
        {/each}    
    </div>
</main>