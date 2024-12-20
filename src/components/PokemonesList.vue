<template>
    <div>
        <form action="" class="box">
            <img :src=imagen alt="" :class="mostrar" />
            <small v-if="inputNone"> {{ nombre }}</small>
            <div v-else>
                <input type="text" v-model="attemp">
                <br /> <br />
                <button type="submit" style="width: 50%; margin: auto;" @click.prevent="descubrir()">Descubrir</button>
            </div>
        </form>
    </div>
</template>
<script>
export default {
    data() {
        return {
            attemp: "",
            mostrar: "unknown",
            inputNone: false,
        }
    },
    props: {
        nombre: String,
        imagen: String
    },
    methods: {
        descubrir() {
            if (this.attemp == this.nombre) {
                this.mostrar = "";
                this.inputNone = true;
                this.$emit("contador")
            } else {
                alert("Lo siento, no es ese Pokémon")
            }
        }
    }

}
</script>

<style scoped>
.box {
    display: flex;
    flex-direction: column;
    width: 30vh;
    margin: 15px;
}

.unknown {
    filter: blur(5px) grayscale(100%);
}
</style>