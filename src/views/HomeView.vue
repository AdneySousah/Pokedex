<script setup>
import { onMounted,reactive,ref,computed } from 'vue';
import ListPokemons from '@/components/ListPokemons.vue';
import CardPokemonSelected from '@/components/CardPokemonSelected.vue'



let pokemons = ref()
let urlBaseSvg= ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/")
let searchPokemonField = ref("")
let pokemonSelected = reactive(ref())
let loading = ref(false)
onMounted(()=>{
  
  /* requisiao API com fetch */
  fetch("https://pokeapi.co/api/v2/pokemon?limit=1400&offset=0")
  .then(res =>res.json()) /* após pegar a requisição transforma em json */
  .then(res => pokemons.value = res.results) /* após transformar em json, armazena na variavel pokemons os resultados */

})

const pokemonsFiltered = computed(()=>{
 
  if(pokemons.value && searchPokemonField.value){
    return pokemons.value.filter(pokemon=>
      pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
    )
  }
  return pokemons.value
})


const selectPokemon = async(pokemon)=>{
  
  loading.value = true
  await fetch(pokemon.url)
  .then(res=> res.json())
  .then(res=> pokemonSelected.value = res)
  .catch(err => alert('Item nao encontrado ou problema com a API contate o desenvolvedor'))
  .finally(()=>{
    loading.value = false
  })
  
}
</script>

<template>
  <main>
    <div class="container text-center">
      <div class="row mt-1">
        <CardPokemonSelected
          :name="pokemonSelected?.name"
          :xp="pokemonSelected?.base_experience"
          :height="pokemonSelected?.height"
          :image = "pokemonSelected?.sprites.other.dream_world.front_default"
          
          :loading ="loading"
          
          ></CardPokemonSelected>
        <div class="col">
          
          <div class="card card-List" >
              <div class="card-body row">
                <div class="mb-3">
                    <label hidden for="searchPokemonField" class="form-label">Pesquisar...</label>
                    <input type="text" class="form-control" id="searchPokemonField" placeholder="Pesquisar..." v-model ="searchPokemonField">
                  </div>
                
                <ListPokemons
                v-for ="pokemon in pokemonsFiltered"
                :key="pokemon.name"
                :name = "pokemon.name"
                :urlBaseSvg ="urlBaseSvg + pokemon.url.split('/')[6]+'.svg'"
                @click="selectPokemon(pokemon)"
                ></ListPokemons>
              </div>
            </div>
          </div>
        </div>
    </div>
  </main>
</template>


<style scoped>
.card-List{
  max-height: 750px;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>