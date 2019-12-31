
<script>
    import {currentPage} from "../stores/stores";
    import Welcome from "../components/Welcome.svelte";
    import {Register} from "../models/Register";
    import {Contact} from '../models/Contact';
    import { fly,fade,slide } from 'svelte/transition';
    import uuid from 'uuid/v4'

    currentPage.set('signup');

    let owner = new Contact();

    let contact = new Contact();

    let listOfContacts = new Array();

    let listOfOwners = new Array();

    let errorOccured = false;

    let error = '';

    function addContact(e){

        e.preventDefault();

        if(contact.Firstname === ''){
            setError('please enter a valid first name');
            return;
        }

        if(contact.Lastname === ''){
            setError('please enter a valid last name');
            return;
        }

        if(contact.Email === ''){
            setError('please enter a valid email address');
            return;
        }

        contact.Id = uuid();
        
        listOfContacts = [...listOfContacts,contact];

        contact = new Contact();
    }

    function addOwner(e){
        e.preventDefault();
        //alert("hello world");
        //return;
        if(!owner.Firstname){
            setError('please enter a valid first name');
            return;
        }

        if(!owner.Lastname){
            setError('please enter a valid last name');
            return;
        }

        if(!owner.Email){
            setError('please enter a valid email address');
            return;
        }

        owner.Id = uuid();
        
        listOfOwners = [...listOfOwners,owner];

        owner = new Contact();
    }

    function removeOwner(e){
        e.stopPropagation();
        let id = e.target.parentElement.getAttribute('key');
        listOfOwners = listOfOwners.filter( (k) => k.Id !== id );
    }

    function setPrimaryOwner(e){
        let key = e.target.getAttribute('key');

        listOfOwners = listOfOwners.map( (e) =>{

            if(e.PrimaryContact){
                e.PrimaryContact = false;
            }

            if(e.Id === key){
                e.PrimaryContact = true;
            }

            return e;

        } );
    }

    function setPrimaryContact(e){
        let key = e.target.getAttribute('key');

        listOfContacts = listOfContacts.map( (e) =>{

            if(e.PrimaryContact){
                e.PrimaryContact = false;
            }

            if(e.Id === key){
                e.PrimaryContact = true;
            }

            return e;

        } );
    }

    function removeContact(e){
        e.stopPropagation();
        let id = e.target.parentElement.getAttribute('key');
        listOfContacts = listOfContacts.filter( (k) => k.Id !== id );
    }

    function setError(message){
        error = message;
        errorOccured = true;
        setTimeout(function(){
            errorOccured = false;
        },5000);
    }

    $:  console.log({
            Owners: listOfOwners.length <= 0 ? "No Owners" : listOfOwners, 
            Contacts: listOfContacts.length <= 0 ? "No Contacts" : listOfContacts
        });

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

    [type="checkbox"].filled-in:checked+label:after {
    
        border: 2px solid #101010!important;
        background-color: #ae191f!important;
        z-index: 0; 
    }
    

    h5{
        background-color: #ae191f;
        width: 100%;
        color:#fff;
        padding: 0.5em;
    }

    .active-custom-chip{
        background-color: #ae191f;
        color: white;
        transition: background-color 0.4s;
    }

    .not-active-custom-chip{
        background-color:rgba(30,30,30,0.2);
        color:rgba(50,50,50,0.8);
        transition: background-color 0.4s;
    }

    .custom-chip{
        display:flex;
        align-items:center;
        font-size:12px;
        border-radius:30px;
        padding:0.8em;width:auto;margin:0.5em;
        cursor: pointer;
    }

   .my-btn{
       border-radius: 30px;
       background-color: #ae191f;
       cursor: pointer;
   }

   .file-field .btn{
       background-color: #ae191f;
   }

   .req{
       color: #ae191f;
   }

   .error-dialog{
       background-color: #101010;
       color: #ec1c24;
       padding:1em;
       position: fixed;
       left:0%;
       top:93.5%;
       width: fit-content!important;
       z-index: 1000;
   }

</style>

<Welcome message={'Ready to deliver?'} image={'/assets/background-img2.jpg'}/>

{#if errorOccured}
    <div in:fly="{{ x:-200, duration: 500, opacity: 0.5}}" out:fly={{x:-200,duration: 500, opacity: 0.5}} class="error-dialog">{error}</div>
{/if}



<div class="container" style="margin-top:2em;">

    <div class="row">

        <div class="col s12">
        
            <h4>Signup Today!</h4>
            <div class="divider"></div>
            <form >

                <div class="row" style="margin-top:2em;">
                    <div class="col s12">
                        <h5>Add Owner(s) / User(s)</h5>
                        <div class="input-field col l6 s12">
                            <input id="firstname" bind:value={owner.Firstname} class="input-field" type="text" validate/>
                            <label for="firstname"><span class="req">*</span> Firstname</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="lastname" bind:value={owner.Lastname} class="input-field" type="text" validate/>
                            <label for="lastname"><span class="req">*</span> Lastname</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="email" bind:value={owner.Email} class="input-field" type="email" validate/>
                            <label for="email"><span class="req">*</span> Email Address</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="phone" bind:value={owner.Phone} class="input-field" type="number" validate/>
                            <label for="phone">Phone Number</label>
                        </div>

                        {#if listOfOwners.length <= 0}
                            <p out:fade={{y: 30, duration: 200, delay: 300}} in:fade={{y: -30, duration: 200, delay: 300}} style="font-style:italic; color:rgba(30,30,30,0.4); padding: 1em;">No owners yet.</p>
                        {:else}
                            <div class="col s12">

                                <div class="row valign-wrapper" style="flex-flow:row wrap!important;">
                                    {#each listOfOwners as own}

                                        <div on:click={setPrimaryOwner} out:fly={{x: 20, duration: 200}} in:fly="{{ x: -20, duration: 200, delay: 300}}" key="{own.Id}" class="custom-chip {own.PrimaryContact ? 'active-custom-chip' : 'not-active-custom-chip'} ">
                                            {`${own.Firstname} ${own.Lastname}`}
                                            <i class="material-icons tiny" on:click={removeOwner} style="padding-left:0.5em;cursor:pointer;">close</i>
                                        </div>

                                    {/each}
                                </div>

                            </div>
                        {/if}

                        <button on:click={addOwner} class="btn center waves-effect waves-light my-btn btn-medium">Add Owner <i class="material-icons right">add</i></button>

                    </div>

                </div>

                <div class="divider"></div>

                <div class="row" style="margin-top:2em;">
                    <div class="col s12">
                        <h5>Company / Franchise Details</h5>
                        <div class="input-field col l6 s12">
                            <input id="companyname" class="input-field" type="text" validate required/>
                            <label for="companyname"><span class="req">*</span> Company Name</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="franchisename" class="input-field" type="text" validate/>
                            <label for="franchisename">Franchise Name</label>
                        </div>

                        <div class="input-field col s12">
                            <input id="street" class="input-field" type="text" validate/>
                            <label for="street"><span class="req">*</span> Street Address</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="city" class="input-field" type="text" validate/>
                            <label for="city"><span class="req">*</span> City</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="state" class="input-field" type="text" validate/>
                            <label for="state"><span class="req">*</span> Parish</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="country" class="input-field" type="text" validate/>
                            <label for="country"><span class="req">*</span> Country</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="zip" class="input-field" type="text" validate/>
                            <label for="zip">Zip Code</label>
                        </div>

                        <div class="file-field input-field col l10 s12">
                            <div class="btn">
                                <span>Company Document(s)</span>
                                <input type="file" multiple>
                            </div>
                            <div class="file-path-wrapper">
                                <input class="file-path validate tooltipped" data-position="top" data-delay="50" data-tooltip="Please note that food handlers permit should be uploaded. It is required." type="text" placeholder="upload all your company document(s) here.">
                            </div>
                        </div>

                        <div class="input-field col l2 s12">
                            <input id="openhours" class="input-field" type="text" validate/>
                            <label for="openhours">Opening Hours</label>
                        </div>

                    </div>

                </div>

                <div class="divider"></div>

                <div class="row" style="margin-top:2em;">
                    <div class="col s12">
                        <h5>Add Contact(s)</h5>
                        <div class="input-field col l6 s12">
                            <input id="firstname1" bind:value={contact.Firstname} class="input-field" type="text" validate/>
                            <label for="firstname1"><span class="req">*</span> Firstname</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="lastname1" bind:value={contact.Lastname} class="input-field" type="text" validate/>
                            <label for="lastname1"><span class="req">*</span> Lastname</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="email1" bind:value={contact.Email} class="input-field" type="email" validate/>
                            <label for="email1"><span class="req">*</span> Email Address</label>
                        </div>

                        <div class="input-field col l6 s12">
                            <input id="phone1" bind:value={contact.Phone} class="input-field" type="number" validate/>
                            <label for="phone1">Phone Number</label>
                        </div>

                        {#if listOfContacts.length <= 0}
                            <p out:fade={{y: 30, duration: 200, delay: 300}} in:fade={{y: -30, duration: 200, delay: 300}} style="font-style:italic; color:rgba(30,30,30,0.4); padding: 1em;">No contacts yet.</p>
                        {:else}
                            <div class="col s12">

                                <div class="row valign-wrapper" style="flex-flow:row wrap!important;">
                                    {#each listOfContacts as con}

                                        <div on:click={setPrimaryContact} out:fly={{x: 20, duration: 200}} in:fly="{{ x: -20, duration: 200, delay: 300}}" key="{con.Id}" class="custom-chip {con.PrimaryContact ? 'active-custom-chip' : 'not-active-custom-chip'} ">
                                            {`${con.Firstname} ${con.Lastname}`}
                                            <i class="material-icons tiny" on:click={removeContact} style="padding-left:0.5em;cursor:pointer;">close</i>
                                        </div>

                                    {/each}
                                </div>

                            </div>
                        {/if}

                        <button on:click={addContact} class="btn center waves-effect waves-light my-btn btn-medium">Add Contact <i class="material-icons right">add</i></button>

                    </div>

                </div>

                <div class="row" style="margin-top:2em;">
                    <div class="col s12">
                        <h5>Additional Information</h5>
                        <p>
                            <input type="checkbox" class="filled-in" id="filled-in-box" checked="" />
                            <label for="filled-in-box">Franchise</label>
                        </p>
                    </div>

                </div>

                <div class="divider" style="margin-bottom:3em;"></div>

                <a href="." class="btn center waves-effect waves-light my-btn btn-large">Sumbit <i class="material-icons right">send</i></a>

            </form>
        </div>

    </div>



</div>