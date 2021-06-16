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
    padding-top: 135px;
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



</style>