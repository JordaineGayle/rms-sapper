
<script type="text/javascript">

    import {currentPage} from "../stores/stores";
 
    import { onMount } from 'svelte';

    import LoginForm from '../components/LoginForm.svelte';

    import Welcome from '../components/Welcome.svelte';

    currentPage.set('home');

    let main;
    
    let height = window.innerHeight;

    let width = window.innerWidth;

    function setBackgroundImage(){
        if(main){
            main.setAttribute('style',`height: ${height}px; width:${width}px`);
        }
    }

    onMount(() => {
        setBackgroundImage();
        window.addEventListener('resize', resizeHandler);
    });

    function resizeHandler() {
        height = window.innerHeight;
        width = window.innerWidth;
        setBackgroundImage();
    }

    
    
</script>


<style>

    .main-area{
        position: relative!important;
        background-image: url('/assets/background-img3.jpg');
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        
    }

    .overlay{
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: rgba(0,0,0,0.4);
        filter: blur(10px);
    }

    .home-content{
        
        height: 100%!important;
        margin: 0px!important;
    }


    .container{
        position: relative!important;
        height: 100%!important;
    }

 </style>


<main bind:this={main} class="main-area">
    
    <div class="overlay"></div>
    <div class="container">
        <div class="row valign-wrapper home-content">
        
            <div class="col l6 offset-l3 m8 offset-m2 s12 offset-s0 ">
                <LoginForm/>
            </div>

        </div>
    </div>

</main>




