<template>

    <div class="row justify-center" style="margin: 60px 0">
        <div class="col-11">
            <div class="row q-col-gutter-lg">
                <div v-for="(text,i) in quote" :key=text class="col-3 ">

                    <div @click="deleteQuote(text)" class="box shadow-5">
                        {{ text }}
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<script>

    export default {
        name: 'quote',
        props: {
            quote: Array,
            deleteQuote: Function
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    .box {
        font-size: 24px;
        font-family: Didot;
        padding: 15px;
        word-wrap: break-word;
    }

</style>
