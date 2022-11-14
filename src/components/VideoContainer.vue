<template>
    <div class="border"></div>
    <div class="video--container">
        <video autoplay playsinline muted loop>
            <source src="@/assets/video/dsktop-header-video.mp4" type="video/mp4">
        </video>
    </div>
    <div class="overlay"></div>
</template>


<script>
    export default {
        name: 'VideoContainer'
    }
</script>