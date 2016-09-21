<template>
    <div>
        <p v-for="pair in pairs">{{pair | json}}</p>
    </div>
</template>

<script>
    export default {
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