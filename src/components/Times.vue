<template>
    <div class="container">
        <time-card v-for="pair in pairs" :timePair="pair"></time-card>
    </div>
</template>

<script>
    import TimeCard from './TimeCard.vue';

    export default {
        components: {
            'time-card': TimeCard
        },
        props: ['model'],
        data () {
            return {
            }
        },
        computed: {
            pairs: function () {
                let pairs = [];

                for (let value of this.model) {
                    if (pairs.length == 0) {
                        pairs.push([value, null]);
                    } else {
                        if (pairs[pairs.length - 1][1] == null) {
                            pairs[pairs.length - 1][1] = value;
                        } else {
                            pairs.push([value, null]);
                        }
                    }
                }

                return pairs;
            }
        }
    }
</script>