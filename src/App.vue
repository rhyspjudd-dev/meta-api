<template>
  <VideoContainer></VideoContainer>
  <div class="container p-4">
    <InputField></InputField>
  </div>
</template>

<script>
import VideoContainer from './components/VideoContainer.vue'
import InputField from './components/InputField.vue'


export default {
  name: 'App',
  components: {
    VideoContainer, InputField
  },
}

</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;500;700&display=swap');

body {
    margin: 0;
    padding: 0;
    height: 100vh;
    width: 100vw;
}

#app {
    height: 100vh;
    width: 100vw;
    position: relative;
    overflow: hidden;
    color: #fefefe;
    font-family: 'Montserrat', sans-serif;
}

.overlay {
    position: absolute;
    inset: 0;
    height: 100vh;
    width: 100vw;
    background: rgb(34,193,195);
    background: linear-gradient(315deg, rgba(34,193,195,1) 0%, rgba(253,187,45,0.3248366878531074) 100%);
    z-index: 3;

    display: grid;
    place-items: center;
    text-transform: uppercase;
}

.border {
    border: 6px solid #fefefe !important;
    position: absolute;
    inset: 2%;
    border-radius: 10px;
    z-index: 50;
    pointer-events: none;
}

.container {
    position: absolute;
    inset: 0;
    z-index: 10;
    display: grid;
    place-items: center;
    z-index: 100;
}

input {
  color: #444F5F;
  cursor: text;
  max-width: 250px;
  transition: 0.25s;
}

input:focus {
  max-width: 280px;
  transition: 0.75s;
  border: #444F5F;
}

a {
  transition: all .2s ease-in-out; 
  color: #e6e6e6;;
  font-size: 0.6rem;
}

a:hover {
  cursor: pointer; 
  color: #444F5F; 
}

.finalMeta {
  display: none;
  text-align: left;
}

button {
  position: relative;
  border: none;
  transition: color 0.5s, transform 0.2s, background-color 0.2s;
  outline: none;
  border-radius: 3px;
  padding: 8px 23px;
  border: 3px solid transparent;
  max-width: 350px;
}

button:active {
  transform: translateY(3px);
}
button::after, button::before {
  border-radius: 3px;
}

.shrink-border {
  background-color: transparent;
  color: #444F5F;
}
.shrink-border:hover {
  background-color: transparent;
  box-shadow: none;
  color: #e6e6e6;
}
.shrink-border::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 3px solid #444F5F;
  transition: opacity 0.3s, border 0.3s;
}
.shrink-border:hover::before {
  opacity: 0;
}
.shrink-border::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: transparent;
  border: 3px solid #e6e6e6;
  opacity: 0;
  z-index: -1;
  transform: scaleX(1.1) scaleY(1.3);
  transition: transform 0.3s, opacity 0.3s;
}
.shrink-border:hover::after {
  opacity: 1;
  transform: scaleX(1) scaleY(1);
}

.fade-in-top {
	-webkit-animation: fade-in-top 0.6s cubic-bezier(0.390, 0.575, 0.565, 1.000) 1s both;
	        animation: fade-in-top 0.6s cubic-bezier(0.390, 0.575, 0.565, 1.000) 1s both;
}
.fade-in-fwd {
	-webkit-animation: fade-in-fwd 0.6s cubic-bezier(0.390, 0.575, 0.565, 1.000) 2s both;
	        animation: fade-in-fwd 0.6s cubic-bezier(0.390, 0.575, 0.565, 1.000) 2s both;
}
.fade-in-bck {
	-webkit-animation: fade-in-bck 0.6s cubic-bezier(0.390, 0.575, 0.565, 1.000) 3s both;
	        animation: fade-in-bck 0.6s cubic-bezier(0.390, 0.575, 0.565, 1.000) 3s both;
}
.fade-in-bl {
	-webkit-animation: fade-in-bl 0.6s cubic-bezier(0.390, 0.575, 0.565, 1.000) 4s both;
	        animation: fade-in-bl 0.6s cubic-bezier(0.390, 0.575, 0.565, 1.000) 4s both;
}
.fade-out-left {
	-webkit-animation: fade-out-left 0.7s cubic-bezier(0.250, 0.460, 0.450, 0.940) both;
	        animation: fade-out-left 0.7s cubic-bezier(0.250, 0.460, 0.450, 0.940) both;
}
.puff-in-center {
	-webkit-animation: puff-in-center 0.7s cubic-bezier(0.470, 0.000, 0.745, 0.715) 2s both;
	        animation: puff-in-center 0.7s cubic-bezier(0.470, 0.000, 0.745, 0.715) 2s both;
}
@-webkit-keyframes fade-in-top {
  0% {
    -webkit-transform: translateY(-50px);
            transform: translateY(-50px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateY(0);
            transform: translateY(0);
    opacity: 1;
  }
}
@keyframes fade-in-top {
  0% {
    -webkit-transform: translateY(-50px);
            transform: translateY(-50px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateY(0);
            transform: translateY(0);
    opacity: 1;
  }
}
 @-webkit-keyframes tracking-in-expand {
  0% {
    letter-spacing: -0.5em;
    opacity: 0;
  }
  40% {
    opacity: 0.6;
  }
  100% {
    opacity: 1;
  }
}
@keyframes tracking-in-expand {
  0% {
    letter-spacing: -0.5em;
    opacity: 0;
  }
  40% {
    opacity: 0.6;
  }
  100% {
    opacity: 1;
  }
}

@-webkit-keyframes fade-in-fwd {
  0% {
    -webkit-transform: translateZ(-80px);
            transform: translateZ(-80px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateZ(0);
            transform: translateZ(0);
    opacity: 1;
  }
}
@keyframes fade-in-fwd {
  0% {
    -webkit-transform: translateZ(-80px);
            transform: translateZ(-80px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateZ(0);
            transform: translateZ(0);
    opacity: 1;
  }
}
@-webkit-keyframes fade-in-bck {
  0% {
    -webkit-transform: translateZ(80px);
            transform: translateZ(80px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateZ(0);
            transform: translateZ(0);
    opacity: 1;
  }
}
@keyframes fade-in-bck {
  0% {
    -webkit-transform: translateZ(80px);
            transform: translateZ(80px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateZ(0);
            transform: translateZ(0);
    opacity: 1;
  }
}

 @-webkit-keyframes fade-in-bl {
  0% {
    -webkit-transform: translateX(-50px) translateY(50px);
            transform: translateX(-50px) translateY(50px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0) translateY(0);
            transform: translateX(0) translateY(0);
    opacity: 1;
  }
}
@keyframes fade-in-bl {
  0% {
    -webkit-transform: translateX(-50px) translateY(50px);
            transform: translateX(-50px) translateY(50px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0) translateY(0);
            transform: translateX(0) translateY(0);
    opacity: 1;
  }
}
@-webkit-keyframes fade-out-left {
  0% {
    -webkit-transform: translateX(0);
            transform: translateX(0);
    opacity: 1;
  }
  100% {
    -webkit-transform: translateX(-50px);
            transform: translateX(-50px);
    opacity: 0;
  }
}
@keyframes fade-out-left {
  0% {
    -webkit-transform: translateX(0);
            transform: translateX(0);
    opacity: 1;
  }
  100% {
    -webkit-transform: translateX(-50px);
            transform: translateX(-50px);
    opacity: 0;
  }
}

@-webkit-keyframes puff-in-center {
  0% {
    -webkit-transform: scale(2);
            transform: scale(2);
    -webkit-filter: blur(4px);
            filter: blur(4px);
    opacity: 0;
  }
  100% {
    -webkit-transform: scale(1);
            transform: scale(1);
    -webkit-filter: blur(0px);
            filter: blur(0px);
    opacity: 1;
  }
}
@keyframes puff-in-center {
  0% {
    -webkit-transform: scale(2);
            transform: scale(2);
    -webkit-filter: blur(4px);
            filter: blur(4px);
    opacity: 0;
  }
  100% {
    -webkit-transform: scale(1);
            transform: scale(1);
    -webkit-filter: blur(0px);
            filter: blur(0px);
    opacity: 1;
  }
}

</style>
