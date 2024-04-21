<script setup>
  import { reactive, ref , toRaw, onMounted} from 'vue';
  import axios from 'axios';

  import { useInfiniteScroll } from '@vueuse/core'

  const baseUrl = ref('https://pokeapi.co/api/v2/')
  const pokemonsEndPoint = ref('pokemon?limit=10')
  const pokemons = ref([])
  const listEl = ref(null)
  const pokemonsToShow = 10


  const getPokemons = async (limit, skip) => {
    const response = await axios.get(
    `https://pokeapi.co/api/v2/pokemon?limit=${limit}&offset=${skip}`
    );
    return response.data.results;
  }

  function getPokemonId(pokemon){
    return pokemon.url.split("/")[6]
  }

  onMounted(() => {
    getPokemons(pokemonsToShow, 0)
  })

  // Change firs letter of pokemon name do upper case
  function toUpper(name){
    return name.replace(/^\w/, (firstLetter) => firstLetter.toUpperCase());
  }


  function showPokemons(){
    console.log(pokemons.value)
  }

  const getPokemonsOnScroll = async () => {
    const newPokemons =  await getPokemons(
      pokemonsToShow,
      pokemons.value.length
    )
    pokemons.value.push(...newPokemons)
  } 

  useInfiniteScroll(
    listEl,
    async () => {
     await getPokemonsOnScroll()
    },
    {distance: 10}
  )
</script>

<template>
  <v-app>
    <v-main class="app">
      <v-container>
        <header >
          <v-form class="d-flex flex-row justify-space-between">
            <v-row class="align-end">
              <v-col cols="12" sm="4" md="3" lg="2" class="d-flex">
                <v-img src="/img/pokemon-23.svg" class="pokemonLogo cursor-pointer mb-1 mb-sm-4"></v-img>
              </v-col>
              <v-col cols="5" sm="3" md="2" lg="2">
                <v-select variant="solo-filled" density="compact" :items="['Nome', 'Id', 'Tipo', 'Espécie']" v-model="filterSelected" placeholder="Filtro"></v-select>
              </v-col>
              <v-col cols="7" sm="5" md="7" lg="8" class="d-flex" >
                <v-text-field class="form__text-field" variant="solo-filled" density="compact" append-inner-icon="mdi-magnify" v-model="searchInput" @click:append-inner="showPokemons" ></v-text-field>
              </v-col>
            </v-row>  
          </v-form>
        </header>
        <div ref="listEl" style="height: 100vh; overflow-y: auto;">
          <v-row>
            <v-col cols="12" sm="6" md="4" lg="3" xl="2" v-for="pokemon in pokemons" >
              <v-card variant="flat" class="card border">
                <v-img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${getPokemonId(pokemon)}.png`" :alt="pokemon.name"
                class="align-end text-black card__img">
                  <v-card-title>{{ toUpper(pokemon.name) }}</v-card-title>
                </v-img>
                <v-card-subtitle class="mb-1 card_subtitle-color">
                  {{ getPokemonId(pokemon).padStart(4, '0') }}
                </v-card-subtitle>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </v-container>
    </v-main>
  </v-app>
</template>

<style>
  .app{
    background-image: linear-gradient(#4B99E3, #3C5AA6);
  }
  .pokemonLogo{
    width: 175px;
    height: 70px;
  }
  .form__text-field .v-field__append-inner:hover{
    cursor: pointer;
  }
  .card{
    background: white;
  }
  .card__img{
    height: 250px;
  }
  .card_subtitle-color{
    color: lightslategray;
  }
  @media screen and (max-width: 959px){
    .v-container{
      max-width: 620px;
    }
  }

  @media screen and (max-width: 599px){
    .v-container{
      max-width: 320px;
    }
  }
</style>