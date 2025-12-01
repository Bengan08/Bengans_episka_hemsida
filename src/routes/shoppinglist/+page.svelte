<script>
    import { fade } from 'svelte/transition'

    let siffror = $state( [{namn: "1", value: "1"},{namn: "2", value: "2"},{namn: "3", value: "3"},{namn: "4", value: "4"},{namn: "5", value: "5"},{namn: "6", value: "6"},{namn: "7", value: "7"},{namn: "8", value: "8"},])

    let varor = $state([{name: 'Mjölk', köpt: false, prio:1}]);
    let lägg_till = $state("");

    function handleSubmit() {
        if (lägg_till.trim() !== "") {
            varor = [...varor, { name: lägg_till, köpt: false }];
            sortera()
            lägg_till = "";
        }
    }
    function taBort(index) {
    varor = varor.toSpliced(index, 1);
}
    function flytta(index){
        varor[index].köpt = !varor[index].köpt;
        varor = [...varor];
    }
    function sortera(index){
        varor = [...varor].sort((a, b) => a.prio - b.prio);
    }
</script>
<main class = container>
<h1>
    Shoppinglist
</h1>
<div class = categories_container>
    <section>
        <h2>
            Behövs köpa
        </h2>
        <ol>
            {#each varor.filter(v => !v.köpt) as vara, i}
                <li transition:fade>
                    {vara.name}
                    <button onclick={() => taBort(i)}>❌</button>
                    <button onclick={() => flytta(i)}>✅</button>
                    <label>Prioritet:</label>
                        <select 
                            bind:value={vara.prio}
                            onchange={() => sortera(i)}
                        >
                            {#each siffror as s}
                                <option value={s.value}>{s.namn}</option>
                            {/each}
                        </select>
                </li>
            {/each}
        </ol>
    <form onsubmit={(event) => { event.preventDefault(); handleSubmit(); }}>
        <label for="lägg_till">Lägg till vara:</label>
            <input type="text" id="lägg_till" bind:value={lägg_till}>
            <input type='submit' value='Lägg Till'>
        </form>
        
    </section>
    <section>
        <h2>
            Har köpts
        </h2>
        <ol>
            {#each varor.filter(v => v.köpt) as vara, i}
                <li transition:fade>
                    {vara.name}
                    <button onclick={() => taBort(i)}>❌</button>
                </li>
            {/each}
        </ol>
    </section>
</div>
</main>


<style>
.container{
    background-color: rgb(227, 54, 250);
    width: 60vw;
    height: 70vh;
    border-radius: 20px;
}
.categories_container{
    display: grid;
    grid-template-columns: repeat(2,1fr);
    gap: 10px;
    background-color: antiquewhite;
    height: 80%;
    display: grid;
    grid-template-rows: 1fr 9fr 1fr;
    
    
}
.categories_container section{
    width: 100%;
    border-radius: 10px;

}

.categories_container section:first-child{  /* vilket barn vill vi styla? */
    background-color: rgba(0, 0, 0, 0.1) /* svart bakgrund med 10% opacitet */
}

.categories_container section:last-child{  /* vilket barn vill vi styla? */
    background-color: rgba(0, 0, 0, 0.3) /* svart bakgrund med 30% opacitet */
}


.container h1{
    color: aqua;
    border-radius: 20px;
    background-color: blueviolet;
    display: flex;
    justify-content: center;
    align-content: center;
    width: 200px;
    padding: 10px;
    margin: 0 auto;

}

.container h2{
    background-color:rgb(0, 0, 139,0.5);
    font-size: medium;
    text-align: center;
    margin: 5%;
    width: 140px;
    margin: 0 auto;
    padding: 10px;
    border-radius: 20px;
}
.container li{
    list-style-type: circle;
    list-style-position: inside;
    border-bottom: 1px solid white;
    padding: 5px;

}

</style>