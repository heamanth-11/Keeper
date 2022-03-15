<template>
    <header>
        <div class="header">
<img src="https://www.gstatic.com/images/branding/product/1x/keep_2020q4_48dp.png" alt=""><span>Keeper</span>
        </div>
    </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style>
header{
    background: #f5ba13;
    box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.3);
    font-family: "McLaren", cursive;
     padding:1rem 0;
    width:100%;
}
header img{
height: 100%;
padding: 0  0 0 2%;
}
.header{
    margin: auto;
}
header span{
    font-size:1.5rem;
    display:inline-block;
    align-items:center;
    font-size: 2rem;
    font-weight:400;
    position: relative;
    bottom: 0.5rem;
    color:white;

}
</style>
