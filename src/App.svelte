<script>
	import Home from './lib/home.svelte';
	import Header from './lib/header.svelte';
	import Loading from './lib/loading.svelte';
	import { key } from './env.js';

	let isRunning = false;
    const supportedLanguages = [];
	let translations = [];

	getSupportedLanguages();

	async function getSupportedLanguages() {
        const response = await fetch(`https://translate.yandex.net/api/v1.5/tr.json/getLangs?key=${key}&ui=en`);
        const data = response.json();
        data.then(data => {
            let [keys, values] = [Object.keys(data.langs), Object.values(data.langs)];
			keys.forEach((key, index) => supportedLanguages.push({name: values[index], code: key}))
		})
	}
	
	async function getTranslations(e) {
		const { value } = e.detail;
        const urls = supportedLanguages.map(language => fetch(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=${key}&text=${value}&lang=${language.code}`));

		isRunning = true;
		
        const responses = await Promise.all(urls);
		const promises = await responses.map(response => response.json());
		const results = await Promise.all(promises);
		translations = results.map(result => result);

		isRunning = false;
	}
</script>

<main>
	<Header on:translate={getTranslations} />
	<Home {translations} {supportedLanguages}/>
</main>

<Loading {isRunning} />