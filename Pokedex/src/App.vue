<script setup>
  import { ref } from 'vue';
  import axios from 'axios';

  const url = "https://pokeapi.co/api/v2/pokemon/pikachu"
  const count = ref(0)

  axios.get(url)
  .then(response => {
    console.log(response.data)
  })
</script>

<template>
  <v-app>
    <v-main class="app">
      <v-container>
        <header class="d-flex flex-column align-center flex-sm-row justify-sm-space-between align-sm-end">
          <img src="/img/pokemon-23.svg" alt="" class="pokemonLogo cursor-pointer mb-4">
        </header>
        <v-row>
          <v-col cols="12" sm="6" md="4" lg="3" xl="2">
            <v-card variant="flat" class="card border">
              <v-img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
              class="align-end text-black card__img">
                <v-card-title>Pikachu</v-card-title>
              </v-img>
              <v-card-subtitle class="mb-1 card_subtitle-color">
                #0025 {{ count }}
              </v-card-subtitle>
            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3" xl="2">
            <v-card variant="flat" class="card">
              <v-img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
              class="align-end text-black card__img">
                <v-card-title>Pikachu</v-card-title>
              </v-img>
              <v-card-subtitle class="mb-1 card_subtitle-color">
                #0025 {{ count }}
              </v-card-subtitle>
            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3" xl="2">
            <v-card variant="flat" class="card">
              <v-img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
              class="align-end text-black card__img">
                <v-card-title>Pikachu</v-card-title>
              </v-img>
              <v-card-subtitle class="mb-1 card_subtitle-color">
                #0025 {{ count }}
              </v-card-subtitle>
            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3" xl="2">
            <v-card variant="flat" class="card">
              <v-img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
              class="align-end text-black card__img">
                <v-card-title>Pikachu</v-card-title>
              </v-img>
              <v-card-subtitle class="mb-1 card_subtitle-color">
                #0025 {{ count }}
              </v-card-subtitle>
            </v-card>
          </v-col>
        </v-row>
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