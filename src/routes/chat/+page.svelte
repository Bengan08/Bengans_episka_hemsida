<script>
    import ElizaBot from 'elizabot';
    import { enhance } from "$app/forms";

    let text = $state('')

    const eliza = new ElizaBot();
    let chat = $state([{ user: 'Eliza', message: eliza.getInitial() }]);

async function write(message) {
    chat.push({user: 'Andvändare', message: text});

//Hämta HTML-elementet med id:et visible
var element = document.getElementById("visible");

//Ändrar elementets CSS-egenskap display till default
element.style.display = "flex"; // Visa elementet

    // random delay for Eliza's response time
    await new Promise((r) => setTimeout(r, 1000 + Math.random() * 1000));

    //TODO: Add Eliza's response to the chat
    chat.push({user: 'Eliza' , message: eliza.transform(text)});
    
    
//Hämta HTML-elementet med id:et visible
var element = document.getElementById("visible");

//Ändrar elementets CSS-egenskap display till default
element.style.display = 'none'; // Visa elementet 


}


</script>

<main class=chatt>
    <section class=messages>
        {#each chat as chatar}
            <article class='article1'>
                <p class={chatar.user}> {chatar.user}: {chatar.message} </p>
        </article>
        {/each}

        <article  id="visible">
            <span class=circle1>
                
            </span>
            <span class=circle1>

            </span>
            <span class=circle1>

            </span>
        </article>
    </section>
    <form method="post"
    use:enhance={({ formElement, formData, action, cancel }) => {
      cancel(); //don't post anything to server
      const text = formData.get("text"); // what does "text" refer to?
    write(text);
    
    formElement.reset();
    
    


    }}> 
        <input type=text class="input" name=input  required placeholder="Skriv ett meddelande" bind:value={text}> 
        
        <div>

        </div>
    </form>

</main>

<style>

    @keyframes typing{
        0% {transform: scale(1)}
        25% {transform:scale(1)}
        50% {transform: scale(1.4)}
        100% {transform: scale(1)}
    }
    main{
        display: grid;
        height: 70vh;
        width: 60vw;
        grid-template-rows: 90% 10%;
        justify-self: center;
        padding: 10px;
        background-color: aquamarine;
        border-radius: 15px;
        max-width: 60vw;

    }

    .messages{
        overflow-y: auto;
        display: flex;
        flex-direction: column;
    }





    .article1{
        display: flex;
        margin: 10px;
        padding: 10px;
        background-color: rgb(222, 230, 171);
        border-radius: 10px;
        max-width: 27.5vw;
        align-self: flex-end;
        font-family:'Courier New', Courier, monospace;
    }

    .article1:nth-child(odd){
        align-self:flex-start;
        background-color: antiquewhite;
    }

        form{
        display: flex;
        
    }

    input{
        display: flex;
        margin: 10px;
        padding: 10px;
        background-color: rgb(222, 230, 171);
        border-radius: 10px;
        width: 55vw;
        position: initial;
        bottom: 10px;
        z-index: 5;
    }



    #visible{
        width: 100px;
        height: 60px;
        min-height: 60px;
        background-color:rgb(255, 255, 255) ;
        display: none;
        border-radius: 10px;
        justify-content: center;
        align-items: center;
        margin-bottom: 4vw;
    }

    .circle1{
        width: 10px;
        height: 10px;
        border-radius: 50%;
        background-color: rgb(0, 0, 0);
        z-index: 15;
        display:flex;
        animation-iteration-count: infinite;
        margin: 7.5px;
        animation-name: typing;
        animation-duration: 1000ms;
        
    }
.circle1:nth-child(1) {
        animation-delay: 0ms; /* Ingen fördröjning */
    }
        /* CSS-stilar för .circle med index 2 (den andra cirkeln) */
.circle1:nth-child(2) {
        animation-delay: 333ms; /* Starta animationen efter 333 millisekunder (ms) */
    }
        /* CSS-stilar för .circle med index 3 (den tredje cirkeln) */
.circle1:nth-child(3) {
        animation-delay: 666ms; /* Starta animationen efter 666 ms */
    }


</style>