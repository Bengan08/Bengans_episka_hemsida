<script>
let cards = $state([
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/4665.png&w=350&h=254", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/5498.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/868.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/864.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/348.png", flipped: false, matched: false },
        { image: "https://www.pngmart.com/files/22/Michael-Schumacher-PNG.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/4396.png", flipped: false, matched: false },
        { image: "https://f1mavericks.com/wp-content/uploads/2025/12/andant01.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/5752.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/5592.png", flipped: false, matched: false },
        { image: "https://cdn.racingnews365.com/_570x570_crop_center-center_none/carsai01.png?v=1741599360", flipped: false, matched: false },
        { image: "https://e1.365dm.com/f1/drivers/256x256/h_full_1548.png", flipped: false, matched: false },

        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/4665.png&w=350&h=254", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/5498.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/868.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/864.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/348.png", flipped: false, matched: false },
        { image: "https://www.pngmart.com/files/22/Michael-Schumacher-PNG.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/4396.png", flipped: false, matched: false },
        { image: "https://f1mavericks.com/wp-content/uploads/2025/12/andant01.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/5752.png", flipped: false, matched: false },
        { image: "https://a.espncdn.com/combiner/i?img=/i/headshots/rpm/players/full/5592.png", flipped: false, matched: false },
        { image: "https://cdn.racingnews365.com/_570x570_crop_center-center_none/carsai01.png?v=1741599360", flipped: false, matched: false },
        { image: "https://e1.365dm.com/f1/drivers/256x256/h_full_1548.png", flipped: false, matched: false },
    ].sort(() => Math.random()- 0.5));

var bluepoints = $state(0)
var redpoints = $state(0)
var blueturn = $state(true);
var flippedCount = 0
var flippedCards = []

    function restart(){
        cards.forEach(card => {
            card.flipped = false
            card.matched = false
        });
        cards.sort(() => Math.random()- 0.5);
        bluepoints = 0
        redpoints = 0
        flippedCards = []
        flippedCount = 0
}

function handelboth(card){
    flip(card)
    gamecheck
}


    function flip(card) {

        if (card.flipped || card.matched) return;

        if (flippedCards.length >= 2) return;

        card.flipped = true;
        flippedCards.push(card);

        // if two cards → check match
        if (flippedCards.length === 2) {
            setTimeout(checkMatch, 1000);
        }
    }


    function checkMatch() {
        const [a, b] = flippedCards;

        if (a.image === b.image) {
            // match!
            a.matched = true;
            b.matched = true;
            flippedCards = []

            if (blueturn) bluepoints++;
            else redpoints++;
        } else {
            // no match → flip back
            a.flipped = false;
            b.flipped = false;

            // switch player
            blueturn = !blueturn;

            flippedCards = []
        }
    }

function gamecheck(){
if (bluepoints+redpoints == 12){
    if (bluepoints>redpoints){
        alert('Blue won')
    }
    else if (bluepoints<redpoints){
        alert('Red won')
    }
    else{
    alert('Game tied')
    }
}
else{return}
}

</script>

<h1>
    Memory
</h1>
<main>
    {#each cards as card}
        <button class="card" class:flipped= { card.flipped } on:click={() => handelboth(card) }  >
            <img class="front" src={card.image}>
            <img class="back" src="https://city-png.b-cdn.net/preview/preview_public/uploads/preview/formula-1-official-white-logo-hd-transparent-background-701751712229658jhzn4h9awp.png">
        </button>
    {/each}



</main>
<div class = 'container1'>
<button class=redo on:click={() => restart()}>
        Restart
    </button>
    </div>
<aside class="blue">
    <p>
        {bluepoints}
    </p>
</aside>

<aside class='red'>
    <p>
        {redpoints}
    </p>
</aside>

<aside class="turn" class:blue={blueturn}>
    
</aside>

<style>
    main{
        display: grid;
        grid-template: repeat(4,100px) / repeat(6,100px);
        justify-content: center;
        gap: 5px;
        

    }
    main > div {
    border: 1px solid black;
    width: 100%;
    height: 100%;
    


}
.card {
    position: relative;
    width: 100%;
    height: 100%;



}
.back:hover{
    transform: scale(1.1);
}
.back::highlight{
    transform: scale(0.9);
}


.container1{
    display: flex;
    justify-content: center;
    margin: 5px;
}
.redo{
    width: 100px;
    height: 40px;
    display: flex;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    justify-content: center;
    align-items: center;


    
}





.card img {
    width: 100%;
    height: 100%;
    object-fit: cover;
        backface-visibility: hidden;

}

.front {
    position: absolute;
    inset: 0;
    display: none;
    transform: rotateY(0deg);
    
}

.back {
    position: absolute;
    inset: 0;
    transform: rotateY(0deg);
    
}

aside.red{
    width: 100px;
    height: 100px;
    position: fixed;
    bottom: 10px;
    right: 10px;
    background-color: red;
    display: flex;
    justify-content: center;
    align-items: center;
}

aside.blue{
    width: 100px;
    height: 100px;
    position: fixed;
    bottom: 10px;
    left: 10px;
    background-color: rgb(100, 8, 248);
    display: flex;
    justify-content: center;
    align-items: center;
    
}

aside.turn{
    box-shadow: 0 0 10px 10px yellowgreen;
    z-index: -1;
    width: 100px;
    height: 100px;
    position: fixed;
    bottom: 10px;
    right: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
}
p{
    font-size: 30px;
}

.card.flipped .front {
    display: block;
}

.card.flipped .back {
    display: none;
}

.card.flipped{
    transform: rotateY(180deg);
}

</style>