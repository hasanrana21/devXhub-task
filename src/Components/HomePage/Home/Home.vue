<template>
    <div id="home-page">
        <div id="dashboard">
            <ul class="dashboard-menu">
                <li @click="dataSubmit = true">Home</li>
                <li>Blog</li>
                <li>About</li>
                <li>Contact</li>
            </ul>
        </div>

        <transition name="slide" appear>

            <transition name="FirstSlider" v-if="dataSubmit">
                <div class="slideAfterClick"> </div>
            </transition>

            <!-- <div class="secondSlideDiv"> -->
            <transition name="secondSlide" v-if="dataSubmit">
                <div class="slideAfterSlide"></div>
            </transition>
            <!-- </div> -->

        </transition>
        
        <Navbar></Navbar>
    </div>
</template>



<script>
import Navbar from '../Navbar/Navbar';
export default {
    data(){
        return{
            submitedButton: true,
            dataSubmit: false,
            showDashboard: false,
        }
    },
    methods: {
        firstSlideClick(){
            this.submitedButton = false;
        }
    },
    components: {
        'Navbar': Navbar
    }
}
</script>



<style scoped>
    #dashboard {
    width: 250px;
    height: 100vh;
    background-color: #22272e;
    color: white;
    z-index: 65;
    }
    .dashboard-menu {
    padding-top: 70px;
    background-color: #22272e;
    }
    .dashboard-menu li {
    list-style: none;
    padding: 10px 0px;
    margin: 15px 15px;
    background-color: goldenrod;
    text-align: center;
    border-radius: 25px;
    font-size: 18px;
    font-weight: 500;
    cursor: pointer;
    }
    .slideAfterClick{
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: -80;
        background-color: #22272e;
    }
    .slideAfterSlide {
        /* position: absolute; */
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 15;
        background-color: red;
        /* width: 1500px;
        margin-right: 0;
        margin-left: -200%;
        margin-top: 16%; */
        /* animation-fill-mode: forwards; */
    }

    /* Transition Part */
    .slide-enter-active,
    .slide-leave-active {
    transition: transform .6s;
    }

    .slide-enter,
    .slide-leave-to {
    transform: translateY(0%) translateX(100vw);
    }
    /* end */
    .FirstSlider-enter-active{
    transition: transform 4s;
    }
    .FirstSlider-leave-active {
    transition: transform .2s;
    }

    .FirstSlider-enter,
    .FirstSlider-leave-to {
        transform: translateY(0%) translateX(100vw);
    }
/* end */
    .secondSlide-enter-active{
    transition: transform 6s;
    }
    .secondSlide-leave-active {
    transition: transform .2s;
    }

    .secondSlide-enter,
    .secondSlide-leave-to {
    transform: translateY(0%) translateX(500vw);
    }

</style>