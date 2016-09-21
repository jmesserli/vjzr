<template>
    <div id="app">
        <nav>
            <a href="/" class="brand-logo center">Vjzr</a>
        </nav>
        <time-input :model="times"></time-input>
    </div>
</template>

<script>
    import TimeInput from './components/TimeInput.vue'

    export default {
        data () {
            return {
                times: []
            }
        },
        components: {
            'time-input': TimeInput
        }
    }
</script>

<style>
    body {
        font-family: sans-serif;
    }
</style>
