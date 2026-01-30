<script>

  // Importera goto-funktionen för att navigera mellan sidor
import { goto } from '$app/navigation';

  // Funktion som hanterar formulärets submit-händelse
function handleSubmit(e) {
    // Förhindra att sidan laddas om (standardbeteende för formulär)
    e.preventDefault();

    
    // Skapa ett FormData-objekt från formuläret
    const formData = new FormData(e.target);
    
    // Hämta värdet från input-fältet med name="search"
    const search = formData.get('search');
    
    // Navigera till den dynamiska routen /search/[pokemon]
    goto('/search/' + search);
    }
    document.addEventListener('DOMContentLoaded', ()=> {
            field.preventDefault();
            let field = document.getElementById('field');
        field.addEventListener('input',()=>{
            sessionStorage.setItem('fieldvalue', field)
        });
    })

    let data = 5
     //sessionStorage.getItem('fieldvalue')

</script>
<main>


<form on:submit={handleSubmit}>
<input type="input" id='field' name="search" placeholder="Sök upp en pokemon" />
</form>

    
    <slot>
        
    </slot>
</main>
<footer>
    <script>
        document.write(data)
    </script>
    
</footer>

<div class="backdrop">

</div>

<style>
    main{
        display: flex;
        height: 80vw;
        width: 100vh;
        background-color: rgb(255, 5, 209,0.8);
        border: 10px;
        border-radius: 12px;
        flex-direction: column;
        margin: 5vh;
        justify-self: center;
        
        

        
    }
    .backdrop{
        width: 100vw;
        height: 100vh;
        background-image: url('https://imageio.forbes.com/specials-images/imageserve/604202ff091b6539cb90fcbc/The-backs-of-a-number-of-Pok-mon-cards-/960x0.jpg?format=jpg&width=960');
        position: fixed;
        background-size: cover;
        top: 0;
        left: 0;
        z-index: -1;
        filter:blur(5px);
        
    }
    form{
        align-self: center;
    }
    input{
        width: 20vw;
        background-color: aquamarine;
        
    }

    footer{
        width: 100%;
        position: fixed;
        background-color: antiquewhite;
    }
</style>