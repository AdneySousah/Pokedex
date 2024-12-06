<script setup>
const pokemon = defineProps(["name","xp","height","image","loading","abilities","weight","stats"])

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
                <strong>Altura: </strong>
                <span>{{pokemon.height}} Metros</span>
            </section><p></p>
            <section class="col">
                <strong>Peso: </strong>
                <span> {{ pokemon.weight}} Kg</span>
            </section><p></p>
            <section class="col">
                <strong class="textHabilidade"> Status</strong>
                <ul class="abilities-list horizontal">
                    <li v-for="(stat,stats, index) in stats" :key="index">
                        {{ stat.stat.name }} {{ stat.base_stat }} 
                    </li>
                </ul>
            </section><p></p>
            <div class="linha"></div>
            <p></p>
            <section class="col">
                <strong class="textHabilidade"> Habilidades</strong>
                <ul class="abilities-list horizontal">
                    <li v-for="(ability, index) in abilities" :key="index">
                        {{ ability.ability.name }}
                    </li>
                </ul>
            </section>
           
        </div>
    </div>
    </div>
  
</template>




<style scoped>
.linha{
    background-color: black;
    width: 10%;
    position: relative;
    height: 5%;
    
}
.row section{
    font-size: 0.8rem;
    
    
}
.cardListPokemon{
background: rgb(252, 90, 69);
background: linear-gradient(90deg, rgb(252, 112, 69) 0%, rgba(253, 29, 29, 0.677m,0.8) 43%, rgb(252, 112, 69,0.8) 100%);
cursor: pointer;

}
.abilities-list {
  display: flex;
  flex-wrap: wrap; 
  list-style: none; 
  padding: 0;
  margin: 0;
  gap: 10px; 
  justify-content: center; 
  align-items: center; 
}

.abilities-list li {
  background: #f2f2f2; 
  padding: 5px 10px; 
  border-radius: 8px; 
  font-size: 14px; 
  font-weight: bold;
  color: #333; 
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); 
}

</style>