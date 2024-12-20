<template lang="">
    <div>
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/404px-International_Pok%C3%A9mon_logo.svg.png">
        <h2>¿Quién es ese Pokémon?</h2>
        <h4>Pokemones descubiertos: <span class="numero">{{numeroPokemones}}</span> </h4>
    </div>
</template>
<script>
export default {
    props: {
        numeroPokemones: Number
    }
}
</script>
<style>
.numero {
    color: coral;
    font-size: x-large;
}
</style>