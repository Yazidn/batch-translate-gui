<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();

    let value;
    function translate() { dispatch('translate', {value}); value = '' }
</script>

<header class="bg-white shadow h-16 px-4 fixed w-full flex justify-between items-center">
    <h1 class="hidden md:inline text-xl mr-8 text-blue-600">codename</h1>
    <div class="flex flex-grow">
        <input class="text-blue-600 p-2 rounded-lg text-indent w-full" type="text" placeholder="Translate i.e. Night" bind:value on:keydown={e => e.which === 13 ? translate() : ''}>
        <button class="hover:bg-blue-600 hover:text-white text-blue-600 bg-white p-2 h-full w-10 rounded-full ml-4" on:click={() => translate() }><i class="fas fa-arrow-right"></i></button>
    </div>
</header>