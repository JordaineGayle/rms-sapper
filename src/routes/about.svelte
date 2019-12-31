<script>
    import {currentPage} from "../stores/stores";
    import Welcome from "../components/Welcome.svelte";
    currentPage.set('about');
</script>

<style>

    .container .row .col p{
        margin-left: 1em!important;
        line-height: 3;
        color: rgba(30,30,30,0.7);
        font-style: italic;
    }


    .container .row .col{
        /* border-left: 4px solid rgba(30,30,30,0.7); */
    }

    .container .row .col:hover{
        /* border-left: 4px solid #ae191f;
        transition: border-left-color 0.4s; */
    }
/* #ae191f; */
</style>


<Welcome message={'Food delivery at it\'s best.'} image={'/assets/background-img3.jpg'}/>

<div class="container" style="margin-top:2em;">

    <div class="row">

        <div class="col s12">
        
            <h4>Our Mission</h4>

            <p>Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.</p>

        </div>

    </div>

    <div class="row">

        <div class="col s12">
        
            <h4>Our Story</h4>

            <p>Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.</p>

        </div>

    </div>

    <div class="row">

        <div class="col s12">
        
            <h4>What we do</h4>

            <p>Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.</p>

        </div>

    </div>



</div>