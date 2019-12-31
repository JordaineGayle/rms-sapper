
<script>
    import {currentPage} from "../stores/stores";
    import Welcome from "../components/Welcome.svelte";
    currentPage.set('contact');
</script>


<style>

    


   /* label focus color */
   .input-field input[type=text]:focus + label,.input-field input[type=email]:focus + label,.input-field input[type=number]:focus + label   {
     color: #ec1c24;
   }

   .input-field input[type=password]:focus + label {
     color: #ec1c24;
   }
   
   
   .input-field input[type=text]:focus,.input-field input[type=email]:focus,.input-field input[type=number]:focus {
     border-bottom: 1px solid #ec1c24;
     box-shadow: 0 1px 0 0 #ec1c24;
   }

   .my-btn{
       border-radius: 30px;
       background-color: #ae191f;
       cursor: pointer;
   }
</style>


<Welcome message={'Having issues with the system?'} image={'/assets/background-img4.jpg'}/>

<div class="container" style="margin-top:2em;">

    <div class="row">

        <div class="col s12">
        
            <h4>Contact Us</h4>
            <div class="divider"></div>
            <form >

                <div class="input-field col l6 s12">
                    <input id="firstname" class="input-field" type="text" validate/>
                    <label for="firstname"><span class="req">*</span> Firstname</label>
                </div>

                <div class="input-field col l6 s12">
                    <input id="lastname" class="input-field" type="text" validate/>
                    <label for="lastname"><span class="req">*</span> Lastname</label>
                </div>

                <div class="input-field col l6 s12">
                    <input id="email" class="input-field" type="email" validate/>
                    <label for="email"><span class="req">*</span> Email Address</label>
                </div>

                <div class="input-field col l6 s12">
                    <input id="phone" class="input-field" type="number" validate/>
                    <label for="phone">Phone Number</label>
                </div>

                <a href="." class="btn center waves-effect waves-light my-btn btn-large">Sumbit <i class="material-icons right">send</i></a>

            </form>
        </div>

    </div>



</div>