<script lang="ts">
import OutputBox from '../OutputBox/OutputBox.vue';
import axios from 'axios';

// interface dataType {
//     url: string,
//     short: string,
//     expiry: Number,
//     rate_limit: Number,
//     rate_limit_reset: Number
// }

let mini: string = "";
export default {
    components: { OutputBox },
    data() {
        return {
            miniURL: "",
            GivenURL: "",
        }
    },
    created() {
        this.miniURL = mini
    },
    methods: {
        async handler(e: any) {
            let data = JSON.stringify({
                "url": this.GivenURL
            });
            let config = {
                method: 'post',
                maxBodyLength: Infinity,
                url: 'http://localhost:3000/api/v1/',
                headers: {
                    'Content-Type': 'application/json'
                },
                data: data
            };

            axios.request(config)
                .then((response) => {
                    console.log(JSON.stringify(response.data));
                    this.miniURL = response.data.short
                })
                .catch((error) => {
                    console.log(error);
                });
        }
    }
}


</script>

<template>
    <div>
        <input class="input" v-model="GivenURL" type="url" name="url" />
        <button @click="handler">Send</button>
        <OutputBox :minifiedURL=miniURL />
        <!-- <component :is="OutputBox" /> -->
    </div>
</template>

<style scoped>
.input {
    min-width: 30vw;
    font-size: 48px;
    border-radius: 18px;
    border: 2px solid white;
    padding: 16px;
    font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
    width: fit-content;
}

.input:focus {
    border: none;
    outline: none;
}
</style>