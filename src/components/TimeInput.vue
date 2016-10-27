<template>
    <div class="container">
        <div class="row">
            <input type="text" placeholder="Zeit hinzufügen..."
                   @keyup="validate"
                   @keyup.enter="onEnter"
                   v-model="input"
                   :class="{invalid: hasError, valid: !hasError}">
        </div>
    </div>
</template>

<script>
    import moment from 'moment';

    export default {
        data () {
            return {
                input: '',
                pattern: /^([01]?\d|2[0-3]):?([0-5]\d)$/,
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
                    return false;
                }
            },
            onEnter: function () {
                if (this.validate()) {
                    let matches = this.pattern.exec(this.input);
                    let concatTime = [matches[1], matches[2]].join(':');
                    this.model.push(moment(concatTime, "HH:mm"));
                    this.model.sort((first, second) => { return first.diff(second); });
                    this.input = '';
                } else {
                    this.hasError = true;
                }
            }
        },
        props: ['model']
    }


</script>