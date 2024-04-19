<script setup>
  import { ref } from 'vue';
  import axios from 'axios';

  const url = "https://pokeapi.co/api/v2/pokemon/pikachu"

  axios.get(url)
  .then(response => {
    console.log(response.data)
  })
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
                <v-select variant="solo-filled" density="compact" class="form__select" :items="['Nome', 'Id', 'Tipo', 'Espécie']" placeholder="Filtro" ></v-select>
              </v-col>
              <v-col cols="7" sm="5" md="7" lg="8" class="d-flex" >
                <v-text-field class="form__text-field" variant="solo-filled" density="compact" append-inner-icon="mdi-magnify"></v-text-field>
              </v-col>
            </v-row>  
          </v-form>
        </header>
        <v-row>
          <v-col cols="12" sm="6" md="4" lg="3" xl="2">
            <v-card variant="flat" class="card border">
              <v-img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
              class="align-end text-black card__img">
                <v-card-title>Pikachu</v-card-title>
              </v-img>
              <v-card-subtitle class="mb-1 card_subtitle-color">
                #0025
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
                #0025
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
                #0025
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
                #0025
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