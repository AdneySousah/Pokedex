<script setup>
const pokemon = defineProps(["name","xp","height","image","loading","skill"])

</script>
<template>

    <div class="card cardListPokemon " :class="loading ? '':'animate__animated animate__flipInX'" style="width: 18rem;">
    <img 
    v-if="pokemon.name" :src="pokemon.image" class="card-img-top" :alt="pokemon.name" height="200"
    >

    <img v-else src="../assets/egg_pokemon.svg" class="card-img-top" :alt="pokemon.name" height="200"
    >
    <div class="card-body">
        <h5 class="card-title text-center">{{ pokemon.name }}</h5>
        <hr>
        <div class="row">
            <section class="col">
                <strong>XP:</strong>
                <span>{{ pokemon.xp }}</span>
            </section>
            <section class="col">
                <strong>Altura:</strong>
                <span>{{pokemon.height}}</span>
            </section>
            <section class="col">
                <strong>Skill:</strong>
                <span>{{pokemon.skill}}</span>
            </section>
        </div>
    </div>
    </div>
  
</template>




<style scoped>
.cardListPokemon{
background: rgb(252, 90, 69);
background: linear-gradient(90deg, rgb(252, 112, 69) 0%, rgba(253, 29, 29, 0.677m,0.8) 43%, rgb(252, 112, 69,0.8) 100%);
cursor: pointer;

}

</style>