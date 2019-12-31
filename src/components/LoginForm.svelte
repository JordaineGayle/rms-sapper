<script>
    import Signup from "../routes/Signup.svelte";

</script>

<style>

    .login-form{
        /* position: fixed; */
        margin-top: 3em;
        background-color: rgba(10,10,10,0.9);
        width:100%;
        height: auto;
        padding: 1em!important;
        border-radius: 10px;
    }

    .input-field input[type=text],.input-field input[type=password]{
        border: none!important;
        color:#fff;
    }

   /* label focus color */
   .input-field input[type=text]:focus + label {
     color: #ec1c24;
   }

   .input-field input[type=password]:focus + label {
     color: #ec1c24;
   }
   /* label underline focus color */
   .input-field input[type=text]:focus {
     border-bottom: 1px solid #ec1c24;
     box-shadow: 0 1px 0 0 #ec1c24;
   }

   
   .input-field input[type=password]:focus {
     border-bottom: 1px solid #ec1c24;
     box-shadow: 0 1px 0 0 #ec1c24;
   }

   .my-btn{
       border-radius: 30px;
       background-color: #ae191f;
       cursor: pointer;
   }
   /* valid color */
   /* .input-field input.valid {
     border-bottom: 1px solid #000;
     box-shadow: 0 1px 0 0 #000;
   } */
   /* invalid color */
   /* .input-field input[type=text].invalid {
     border-bottom: 1px solid #000;
     box-shadow: 0 1px 0 0 #000;
   } */
   /* icon prefix focus color */
  
   .req{
       color: #ae191f;
   }

   .plinks p{
       cursor: pointer;
   }

   .plinks p a{
       color: #ec1c24;
       font-size: 12px;
       text-decoration: underline;
   }


</style>


<form class="col s12 login-form center z-depth-4" >
    
    <div class="row">

        <div class="input-field col s12">
            <input id="company" class="input-field" type="text" validate/>
            <label for="company"><span class="req">*</span> Company Code</label>
        </div>

        <div class="input-field col s12">
            <input id="fran" class="input-field" type="text" validate/>
            <label for="fran">Franshise Code</label>
        </div>

        <div class="input-field col s12">
            <input id="username" class="input-field"  type="text" validate/>
            <label for="username"><span class="req">*</span> Username</label>
        </div>
        
        <div class="input-field col s12">
            <input id="password" class="input-field" type="password" validate/>
            <label for="password"><span class="req">*</span> Password</label>
        </div>

    </div>

    <a href="." class="btn center waves-effect waves-light my-btn btn-large">Login <i class="material-icons right">send</i></a>

    <div class="col s12 plinks">
        <p class="center-align white-text" style="width:100%;"><a href='/signup'>Forgot password</a> | <a href='/signup'>Signup</a></p>    
    </div>
</form>