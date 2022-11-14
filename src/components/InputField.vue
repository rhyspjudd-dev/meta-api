<template>
    <section class="form">
        <form onsubmit="return false">
            <div class="h1 text-wrap mb-4 fade-in-top">See a links top level SEO meta data.</div>
            <div class="mb-3">
                <input type="text" name="site" placeholder="https://" value="https://" class="form-control user-input mb-2 fade-in-fwd" id="exampleInputText">
            </div>
            <button type="submit" @submit.prevent v-on:click="getUserinput(), updateEl()" class="mb-4 shrink-border fade-in-bck">Submit</button>
        </form>
        <p class="link-text fade-in-bl">API Powered by <a href="https://www.linkpreview.net/" target="_blank">linkpreview.net</a></p>
    </section>
    <section class="finalMeta">
        <h1 class="metaTitle h1"></h1>
        <div class="metaDescription"></div>
        <a class="metaUrl"></a>
        <button type="reload" v-on:click="reload()" class="mt-4 mb-4 shrink-border fade-in-bck">Go again!</button>
    </section>
</template>


<script>
    import { getUserinput } from '@/App.vue'

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
                //alert(response.description),
                show(response)
     
                )
                .catch(err => console.error(err));
            },
        updateEl() {
            const form = document.querySelector("form");
            const formSection = document.querySelector(".form");
            form.classList.add('fade-out-left');
            const linkText = document.querySelector(".link-text");
            linkText.classList.add('fade-out-left');
            setTimeout(() => {
                formSection.style.display = 'none';
            }, 1500);
        }, 
        reload() {
            location.reload();
        }  
        }
    }

    function show(response) {
        setTimeout(() => {
            const finalMeta = document.querySelector(".finalMeta")
            finalMeta.style.display = 'grid';
            finalMeta.classList.add('puff-in-center')
        }, 500);

        // Update title
        const finalTitleEl = document.querySelector(".metaTitle")
        const metaTitle = response.title
        finalTitleEl.innerHTML = metaTitle 
        // Update Description
        const finalDescriptionEl = document.querySelector(".metaDescription")
        const metaDescription = response.description
        finalDescriptionEl.innerHTML = metaDescription;
        // Update Url
        const finalUrlEl = document.querySelector(".metaUrl")
        const metaUrl = response.url
        finalUrlEl.innerHTML = metaUrl;

    } 
</script>

<style>

.finalMeta {
    display: none;
}

</style>