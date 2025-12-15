<script>
function enlarge(){
    const boxar = document.querySelectorAll(".boxar");
    boxar.forEach(box => {
        box.style.width = "150px";
        box.style.height = "150px";
    });
}
function small(){
    const boxar = document.querySelectorAll(".boxar");
    boxar.forEach(box => {
        box.style.width = "100px";
        box.style.height = "100px";
    });
}
</script>

<main>
    

    <div class="rutnat" on:mouseover={enlarge} on:mouseleave={small}>
        <div class="boxar">1</div>
        <div class="boxar">2</div>
        <div class="boxar">3</div>
        <div class="boxar">4</div>
        <div class="boxar">5</div>
        <div class="boxar">6</div>
    </div> 
</main>

<style>
.rutnat {
    display: grid;
    grid-template: repeat(2, 100px) / repeat(3,100px);
    gap: 10px;
}

.boxar {
    background: lightgray;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 40px;
    width: 100px;
    height: 100px;
}
</style>
