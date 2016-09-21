<template>
    <div class="container">
        <div class="row">
            <input type="text" placeholder="Zeit hinzufügen..." @keyup="validate"
                   @keyup.enter="onEnter"
                   v-model="input" :class="{invalid: hasError, valid: !hasError}">
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                input: '',
                pattern: /(0?\d|1\d|2[0-3]):?([0-5]\d)/,
                hasError: false
            }
        },
        methods: {
            validate: function () {
                if (this.pattern.test(this.input)) {
                    this.hasError = false;
                    return true;
                } else {
                    this.hasError = true;
                    return true;
                }
            },
            onEnter: function () {
                if (this.validate()) {
                    this.model.push(this.input);
                    this.input = '';
                } else {
                    this.hasError = true;
                }
            }
        },
        props: ['model']
    }
</script>