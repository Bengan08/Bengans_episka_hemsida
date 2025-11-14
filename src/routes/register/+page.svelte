<script>
    import { onMount } from 'svelte';
    import {users_store} from "$lib/user";
    let users = [];

    let color = 'black'
    let email = ''
    let namn = ''
    let lösen = ''
    let colors = [{namn: "Blå", value: "blue"}, {namn: "Röd", value: "red"}, {namn: "Grön", value: "green"}, {namn: "Gul", value: "Yellow"}, {namn: "Svart", value: "black"}, {namn: "Rosa", value: "pink"}, {namn: "Lila", value: "purple"}, {namn: "Orange", value: "orange"}, {namn: "Brun", value: "brown"},{namn: "Turkos", value: "turquoise"},{namn: "Grå", value: "gray"},{namn: "Vit", value: "white"},{namn: "Koral", value: "coral"},{namn: "Indigo", value: "indigo"},{namn: "Magenta", value: "magenta"}]
    
    function handleSubmit(event) {
        let new_user = { username: namn, password: lösen, email: email, color: color };

    // Kolla om användarnamnet redan finns
    const matches = users.filter(u => u.username === new_user.username);

    if (matches.length === 0) {
        users = [...users, new_user];
        $users_store = JSON.stringify(users);

        alert(`Välkommen. Ditt namn: ${namn}, Din Email: ${email}, Ditt lösenord: ${lösen}`);
    } else {
        alert("Användarnamnet är redan taget!");
    }
}

</script>
<main>
<div>
    <div class='container'>
        <h1>
            Regestering
        </h1>
        <form on:submit|preventDefault={handleSubmit}>
            <div style="width: 100px; height: 100px; border-radius: 50%; overflow:hidden; background-color:{color};">

            </div>
            <label for="name">Namn:</label>
            <input type="text" id="name" bind:value={namn}>

            <label for="email">Email:</label>
            <input type="email" id="email" bind:value={email} >
            
            <label for="password">Password:</label>
            <input type="password" id="password" bind:value={lösen} >
            
            <label for="favoritfärg">Favoritfärg:</label>
            <select id="favoritfarg" name="favoritfarg" bind:value={color}>
                {#each colors as colo}
                <option value={colo.value}>{colo.namn}</option>
                {/each}
            </select>
            <input type='submit' value='Registrera'>
        </form>
        <a href="/login">Har du redan konto?</a>
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
        min-height: 500px;
        min-height: 500px;
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
        background-color: #cf51da;
        margin: auto;
        min-width: 300px;
        min-height: 500px;
}     
        
</style>
