<template>
  <div>
    <v-row>
      <v-col class="text-center">
        <h1>Personajes</h1>
        <!-- Personaje es: {{ morty }} -->
        <!-- <ul>
        <li
          v-for="(personaje, $index) in $store.state.personajes.characters"
          :key="$index"
        >
          {{ personaje }}
        </li>
      </ul> -->
      </v-col>
    </v-row>
    <v-container>
      <v-row no-gutters>
        <!-- morty -->
        <v-card class="pa-2" outlined tile>
          <v-img :src="mortyImg"></v-img>
          <v-card-title>{{ mortyName }}</v-card-title>
        </v-card>

        <!-- rick -->
        <v-card class="pa-2" outlined tile>
          <v-img :src="rickImg"></v-img>
          <v-card-title>{{ rickName }}</v-card-title>
        </v-card>

        <!-- summer -->
        <v-card class="pa-2" outlined tile>
          <v-img :src="summerImg"></v-img>
          <v-card-title>{{ summerName }}</v-card-title>
        </v-card>

        <!-- beth -->
        <v-card class="pa-2" outlined tile>
          <v-img :src="bethImg"></v-img>
          <v-card-title>{{ bethName }}</v-card-title>
        </v-card>

        <!-- jerry -->
        <v-card class="pa-2" outlined tile>
          <v-img :src="jerryImg"></v-img>
          <v-card-title>{{ jerryName }}</v-card-title>
        </v-card>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  // SSR
  async asyncData({ $axios }) {
    const getCharacters = await $axios.$get(
      "https://rickandmortyapi.com/api/character"
    );

    // Characters
    const mortyName = getCharacters.results[1].name;
    const mortyImg = getCharacters.results[1].image;

    const rickName = getCharacters.results[0].name;
    const rickImg = getCharacters.results[0].image;

    const summerName = getCharacters.results[2].name;
    const summerImg = getCharacters.results[2].image;

    const bethName = getCharacters.results[3].name;
    const bethImg = getCharacters.results[3].image;

    const jerryName = getCharacters.results[4].name;
    const jerryImg = getCharacters.results[4].image;

    return {
      mortyName,
      mortyImg,
      rickName,
      rickImg,
      summerName,
      summerImg,
      bethName,
      bethImg,
      jerryName,
      jerryImg
    };
  },
  data: () => ({
    // mortyName: null
  }),
  methods: {},
  mounted() {}
};
</script>

<style></style>
