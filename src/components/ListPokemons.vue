<script setup>
    const pokemon = defineProps(["name","urlBaseSvg"])


</script>

<template>
  <div class="col-4">
    <div class="card p-2 mb-3 cardListPokemon">
        <p class="text-center">{{ pokemon.name  }}</p>
        <img :src="urlBaseSvg" class="card-img-top" alt="" width="80px" height="80px">
    </div>
  </div>
</template>



<style scoped>
.cardListPokemon{
background: rgb(69,228,252);
background: linear-gradient(90deg, rgba(69,228,252,1) 0%, rgba(29,58,253,0.676908263305322) 43%, rgba(69,228,252,1) 100%);
cursor: pointer;
}
.cardListPokemon:hover{

    background: linear-gradient(90deg, rgba(69,228,252,1) 0%, rgba(29,58,253,0.976908263305322) 43%, rgba(69,228,252,1) 100%);
}

.cardListPokemon img:hover{
    padding: .2rem;
    transition: 0.2s;
}

</style>