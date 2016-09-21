<template>
    <div id="app">
        <nav>
            <a href="/" class="brand-logo center">Vjzr</a>
        </nav>
        <time-input :model="times"></time-input>
        <times :model="times"></times>
    </div>
</template>

<script>
    import TimeInput from './components/TimeInput.vue';
    import Times from './components/Times.vue';

    export default {
        data () {
            return {
                times: []
            }
        },
        components: {
            'time-input': TimeInput,
            'times': Times
        }
    }
</script>

<style>
    body {
        font-family: sans-serif;
    }
</style>
