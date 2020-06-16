<script>
    import tinycolor from 'tinycolor2';

    export let text;
    export let lang;
    export let language;

    let color = tinycolor.random();
    let [color1, color2] = ['', '']
    if (color.isLight()) [color1, color2] = [color.darken(40).toHexString(), color.lighten(15).toHexString()];
    else if (color.isDark()) [color1, color2] = [color.toHexString(), color.lighten(15).toHexString()];

</script>

<div class="flex items-center justify-center text-white shadow-md" style="background: linear-gradient(45deg, {color1}, {color2})">
    <div class="p-4">
        <h3>{text}</h3>
        <p>{lang}, {language}</p>
        <a target="_blank" href="https://translate.yandex.com/">Powered by Yandex. Translate</a>
    </div>
</div>
