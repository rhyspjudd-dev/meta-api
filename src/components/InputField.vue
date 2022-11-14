<template>
    <section class="form">
        <form onsubmit="return false">
            <div class="h1 text-wrap mb-4 fade-in-top">See a links top level SEO meta data.</div>
            <div class="mb-3">
                <input type="text" name="site" placeholder="http://" value="http://" class="form-control user-input mb-2 fade-in-fwd" id="exampleInputText">
            </div>
            <button type="submit" @submit.prevent v-on:click="getUserinput(), updateEl()" class="mb-4 shrink-border fade-in-bck">Submit</button>
        </form>
        <p class="link-text fade-in-bl">API Powered by <a href="https://www.linkpreview.net/" target="_blank">linkpreview.net</a></p>
    </section>
    <section class="finalInfo">

    </section>
</template>


<script>
    import { getUserinput } from '@/App.vue'
// import { response } from 'express';

    export default {
        name: 'InputField',
        components: {
            getUserinput
        },
        methods: {
        getUserinput () {
            const userInput = document.querySelector(".user-input").value;
            console.log(userInput)
            const options = {method: 'GET', headers: {accept: 'application/json'}};

            fetch('http://api.linkpreview.net/?key=fdd563e42cde3abcf84d9e7f28a624d9&q=' + userInput, options)
                .then(response => response.json())
                // .then(response => console.log(response))
                .then(response => 
                alert(response.description)
                //displayMeta(response)
                )
                .catch(err => console.error(err));
            },
        updateEl() {
            const form = document.querySelector("form");
            form.classList.add('fade-out-left');
        },
        }
    }
</script>

<style>

.finalInfo {
    display: none;
}

</style>