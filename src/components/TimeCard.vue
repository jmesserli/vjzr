<template>
    <div class="card">
        <div class="card-content black-text">
            <span class="card-title">{{ firstString }} - {{ secondString }}</span>
        </div>
        <div class="card-action">
            <p>{{ timeString }}</p>
        </div>
    </div>
</template>

<script>
    import moment from 'moment';

    export default {
        props: ['timePair'],
        data() {
            return {
                intervalId: -1,
                currentTime: null
            }
        },
        created () {
            console.log('timecard ready');
            if (this.timePair[1] == null) {
                this.currentTime = moment();

                let self = this;
                this.intervalId = setInterval(function () {
                    console.log('updating time');
                    self.$data.currentTime = moment();
                }, 1000);
            }
        },
        destroyed () {
            if (this.intervalId !== -1) {
                clearInterval(this.intervalId);
            }
        },
        computed: {
            'firstString': function () {
                return this.timePair[0].format('HH:mm');
            },
            'secondString': function () {
                let secondMoment = this.timePair[1];
                if (secondMoment === undefined || secondMoment === null) {
                    return '(now)';
                } else {
                    return secondMoment.format('HH:mm');
                }
            },
            'timeString': function () {
                let secondMoment = this.timePair[1];
                let isNow = false;

                if (secondMoment === undefined || secondMoment === null) {
                    isNow = true;
                    secondMoment = this.currentTime;
                }

                let result = Math.round(secondMoment.diff(this.timePair[0]) / 36000) / 100 + ' h';

                if (isNow) {
                    return '(' + result + ')';
                } else {
                    return result;
                }
            }
        }
    }
</script>