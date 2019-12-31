<script>
    import {currentPage as cur} from "../stores/stores";
</script>

<style>

    .navElements{
        background-color: #101010;
        z-index: 100;
        width: 100%;
        padding: 0px!important;
    }

    .navElements a, #mobile-demo a{
        background-color: none;
        transition:background-color 0.4s ease-in;
        color:white;
        padding-left: 1em!important;
        padding-right: 1em!important;
    }

    .navElements a:hover, #mobile-demo a:hover{
        background-color: #ec1c24;
        transition:background-color 0.4s ease-in;
    }

    .active-nav{
        background-color: #ae191f!important;
    }

    .logo{
        color: #ae191f;
        font-family: 'Permanent Marker', cursive;
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        padding: 0px!important;
        margin: 0px!important;
    }

    .logo1{
        color: #ae191f;
        font-family: 'Permanent Marker', cursive;
        display: flex;
        justify-content: flex-start;
        width: 100%!important;
        flex-flow: row nowrap;
        align-items: center;
        padding: 0px!important;
        margin: 0px!important;
        background-color: #080808
    }

    #hamburger{
        padding-left:1em!important;
        padding-right:1em!important;
        margin:0px!important;
    }

    .navbar-fixed{
        margin: 0px!important;
        position: fixed!important;
    }

    #mobile-demo{
        position: fixed ;
        background-color: #101010;
         z-index: 1000!important;
    }
    
</style>

<div class="navbar-fixed">
    <nav class="navElements">
        <div class="nav-wrapper">
            <a id="hamburger" href="." data-activates="mobile-demo" class="button-collapse"><i class="material-icons">menu</i></a>
            <p class="brand-logo logo hide-on-med-and-down"><img src="assets/logo.png" alt="no image" width="80"/> RMS</p>
            <!-- .show-on-medium-and-down -->
            <ul id="nav-mobile" class="right hide-on-med-and-down">
                <li><a class="{$cur === 'home' ? 'active-nav' : ''}" href='.'>Home</a></li>
                <li><a class="{$cur === 'about' ? 'active-nav' : ''}" href='about'>About Us</a></li>
                <li><a class="{$cur === 'contact' ? 'active-nav' : ''}" href='contact'>Contact</a></li>
                <li><a class="{$cur === 'signup' ? 'active-nav' : ''}" href='signup'>Sign up</a></li>
            </ul>
        </div>
    </nav>
</div>

<ul class="side-nav" id="mobile-demo">
    <h5 class="brand-logo logo1"><img class="responsive-img" src="assets/logo.png" alt="no image" width="98"/> RMS</h5>
    <li><a class="{$cur === 'home' ? 'active-nav' : ''}" href='.'>Home</a></li>
    <li><a class="{$cur === 'about' ? 'active-nav' : ''}" href='about'>About Us</a></li>
    <li><a class="{$cur === 'contact' ? 'active-nav' : ''}" href='contact'>Contact</a></li>
    <li><a class="{$cur === 'signup' ? 'active-nav' : ''}" href='signup'>Sign up</a></li>
</ul>
  




