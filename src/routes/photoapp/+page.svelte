<script>
    
let image = "https://picsum.photos/id/70/367/267"
let photo = "isak_skido.jpg"
let picture = "https://picsum.photos/id/93/367/267"
</script>


<h1> Photoapp </h1>
<p>  Denna sida innehåller <strong> fina </strong> bilder </p>

<div class='photos'>
    <div class='image-wrapper'>

        <img src={image} alt='Isak Bengtsson som kör skidorientering'
        >
        </div>
    <div class='image-wrapper'>
        <img src={photo} alt='Jukola lagbild 2025'
        >
        </div>
    <div class='image-wrapper'>
        <img src={picture} alt='jabbathehut'
        >
        </div>
    </div>

<style>
    .photos{
        display:flex;
        flex-wrap:wrap;
        max-width:90vw;
        align-items:center;
        justify-content:center;
        
    }
    .photos img{
        width:100%;

    }
    .image-wrapper{
        flex:0 0 300px;
        margin:10px;
        background-color: gainsboro;
        border-radius: 20px;
        
        
    }

    .image-wrapper img{
        width: 100%;
        border-radius: 20px;
        box-shadow: 4px 8px 10px rgba(0,0,0,0.2);
        
    }
    .image-wrapper:hover { flex:2; }
    .image-wrapper:active { transform: scale(0.9); }

    
h1{
    text-align: center;
    font-size: 50px;
    margin: 20px;
    color: grey;
}
p{
    text-align: center;
    font-size: 25px;
    margin: 20px;
    color: grey;
}
    



</style>

