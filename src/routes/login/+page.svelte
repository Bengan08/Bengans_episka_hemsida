<script>
    import { onMount } from 'svelte';
    import {users_store} from "$lib/user";
    let users = [];
    $users_store

    // Importera och initiera users-listan när komponenten laddas
    onMount(() => {
        if ($users_store && $users_store.length > 2) {
            users = JSON.parse($users_store);
        } else {
            users = [];
        }
    });

    let color = 'black'
    let email = ''
    let lösen = ''
    let namn = ''

    
    function handleSubmit(event) {
    const user = users.find(u => u.username === namn && u.password === lösen);

    if (user) {

        alert(`Välkommen in ${namn}`);
    } else {
        alert("Fel andvändarnamn eller lösenord");
    }
}

</script>
<main>
<div>
    <div class='container'>
        <h1>
            Inloggning
        </h1>
        <form on:submit|preventDefault={handleSubmit}>
            <div>
            
            </div>
            <label for="name">Namn:</label>
            <input type="text" id="name" bind:value={namn}>
            
            <label for="password">Password:</label>
            <input type="password" id="password" bind:value={lösen} >
            <div class='inloggning'>
                <input type='submit' value='Logga in'>
            </div>
        </form>
        <a href="/register">Har du ej konto?</a>
    </div>
</div>
</main>

<style>
main{
        background-image: url("https://t4.ftcdn.net/jpg/05/21/65/59/360_F_521655929_N80d5GaCQJ2VP073PfTXJTe9mkvsNtHE.jpg");
        background-size: cover;
        width: 100%;
        height: 100%;
        padding: 5%;
        min-height: 300px;
        min-height: 300px;
    }

.container{
        display:flex;
        flex-direction:column;
        justify-content:space-evenly;
        align-items:center;
        border: solid 5px rosybrown;
        border-radius: 10px;
        width: 35%;
        height: 80%;
        background-color:#cf51da;
        margin: auto;
        min-width: 300px;
        min-height: 200px;
}     
.inloggning{
    display:flex;
    flex-direction:column;
    justify-content:space-evenly;
    align-items:center;
    padding: 5%;
}
        
</style>