<script>


    import { fly,fade,slide } from 'svelte/transition';

    import {onMount} from 'svelte';

    export let message = 'Welcome to my component';

    export let image = "";
    
    let visible = false;

    onMount(()=>{
        setTimeout(function(){
            visible = true;
    },200);
    });

</script>

<style>

    main{
        position: relative;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        height: 400px;
        display: flex;
        flex-flow: row wrap;
        
    }

    main h3{
        color: #fff;
        margin-top: 4em;
        margin-bottom: 3em;
        position: relative;
        padding: 0.5em;
        /* border-left: 2px solid white; */
        font-style: italic;
    }

    .overlay{
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: rgba(0,0,0,0.6);
    }

    

</style>

<main style="background-image: url({image});">
    <div class="overlay"></div>
    <div class="container">
    
        <div class="row">
            {#if visible}
                <h3 in:fly="{{ x: -200, duration: 200, delay: 300}}">{message}</h3>
            {/if}
        </div>

    </div>
</main>