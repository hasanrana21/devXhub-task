<template>
    <div>
        <div class="login-btn-div">
            <button class="login-button" @click="showModal = true">Login</button>
        </div>

        <transition name="fade"  v-if="showModal" @click="showModal = false">
            <div class="modal-overlay"></div>
        </transition>

        <transition name="slide" appear>
            <div id="modalClass" :class="dataSubmit ? 'modalClass2' : '' " v-if="showModal">
                <div class="text-end">
                    <button class="cross-button" v-if="showModal" @click="showModal = false">X</button>
                </div>

                        <!-- <div> -->
                <transition name="formInputs" v-if="!dataSubmit">
                    <form v-on:submit.prevent class="form-inputs">
                            <div class="mb-3">
                                <label for="exampleInputEmail1" class="form-label">Email Address</label><br>
                                <input type="email" name="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
                            </div>

                            <div class="mb-3">
                                <label for="exampleInputPassword1" class="form-label">Password</label><br>
                                <input type="password" name="password" class="form-control" id="exampleInputPassword1">
                            </div>
                    </form>   
                </transition>    
                        <!-- </div> -->
                    
                <div class="submit-button-div">

                        <button class="text-hide" v-if="dataSubmit"> </button>
                        
                        <button type="submit"
                        :class="dataSubmit ? 'sendDiv' : 'text-center'"
                        @click="dataSubmit = true" 
                        id="submit-button"
                        v-if="!dataSubmit">
                            <span>Submit</span> 
                        </button>

                </div>

                <div :class="dataSubmit ? 'secondSliderDiv' : '' ">
                    <div :class="dataSubmit ? 'secondSlider' : '' "></div>
                </div>
            </div>
        </transition>
    </div>
</template>



<script>
export default {
    data(){
        return{
            showModal: true,
            submitedButton: true,
            dataSubmit: false,
        }
    },
    methods: {
        firstSlideClick(){
            this.submitedButton = false;
        }
    }
    
}
</script>

<style>
    .login-button{
        border: none;
        padding: 10px 25px;
        border-radius: 5px;
        background-color:crimson;
        color: white;
        font-size: 18px;
        font-weight: 700;
        width: 100px;
        height: 50px;
        margin-right: 40px;
        margin-top: 15px;
        cursor: pointer;
    }
    .login-btn-div{
        margin-top: -45%;
    }

    .secondSliderDiv {
        margin-left: 100%;
        animation-name: secondSlideDiv;
        animation-fill-mode: forwards;
        animation-duration: 4s;
        animation-delay: 5s;
        margin-top: -43%;
    }
    @keyframes secondSlideDiv {
        0%{
            margin-left: 100%;
        }
        100%{
            margin-left: -223%;
        }
    }

    .secondSlider {
        background-color: #44474f;
        height: 100vh;
        width: 100%;
    }
    .text-hide {
        padding: 22px 68px;
        background-color: goldenrod;
        border: none;
        border-radius: 4px;
        
        text-align: center;
        animation-name: buttonDiv2;
        animation-duration: 2s;
        animation-fill-mode: forwards;
        animation-delay: 1s;
    }
    @keyframes buttonDiv2 {
        0%{
            margin-top: 140px;
        }
        100%{
            margin-top: 0px;
            border-radius: 50px;
            padding: 18px 20px;
        }
    }


    .modal-overlay{
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: -5;
        background-color: rgba(0, 0, 0, .5);
    }

    #modalClass{
        position: fixed;
        right: 0;
        top: 0;
        z-index: 99;
        height: 100vh;
        width: 350px;
        background-color: #22272e;
        color: white;
        border-radius: 4px;
        padding: 30px;
        padding-right: 0;
        
    }
    .modalClass2{
        animation-name: modal;
        animation-duration: 4s;
        animation-fill-mode: forwards;
    }
    @keyframes modal {
        0%{
            padding-left: 0%;
        }
        100%{
            padding-left: 57%;
        }
    }
    .form-inputs {
        text-align: left;
        height: 30vh;
    }
    .form-inputs input{
        width: 300px;
        font-size: 19px;
        padding: 8px 0;
        margin-top: 10px;
        margin-bottom: 25px;
    }
    .slideAfterSlide {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 99;
        background-color: #44474f;
        width: 1500px;
        margin-right: 0;
        margin-left: -200%;
        margin-top: 16%;
        animation-fill-mode: forwards;
        animation-name: animation-second-slide;
    }

    .submit-button-div{
        text-align: center;
        height: 50px;
        margin-top: 70px;
    }

    #submit-button{
        padding: 11px 40px;
        background-color: goldenrod;
        border: none;
        border-radius: 4px;
        color: white;
        font-size: 18px;
        cursor: pointer;
    }


    .cross-button{
        border: none;
        font-size: 21px;
        font-weight: 700;
        color: red;
        padding: 0 10px;
        border-radius: 4px;
        margin-bottom: 35px;
        margin-right: 30px;
        cursor: pointer;
    }

    .sendDiv{
        text-align: center;
        animation-name: buttonDiv;
        animation-duration: 2s;
        animation-fill-mode: forwards;
        animation-delay: 1s;
    }
    @keyframes buttonDiv {
        0%{
            margin-top: 156px;
        }
        100%{
            margin-top: 0px;
        }
    }


/* Transition Effect Start */
    .fade-enter-active,
    .fade-leave-active{
        transition: opacity 0.5s;
    }

    .fade-enter,
    .fade-leave-to{
        opacity: 0;
    }
/* end */

    .slide-enter-active,
    .slide-leave-active {
        transition: transform .6s;
    }

    .slide-enter,
    .slide-leave-to {
        transform: translateY(0%) translateX(100vw);
    }

/* Form Input */
    .formInputs-leave-active {
        transition: opacity 1s;
    }

    .formInputs-leave-to {
        opacity: 0;
    }
</style>