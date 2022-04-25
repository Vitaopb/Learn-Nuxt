<template>
  <v-card>
    <v-list>
      <v-subheader>Heros Star Wars</v-subheader>
      <v-expansion-panels>
        <v-expansion-panel v-for="(item, i) in heros.results" :key="i">
          <v-expansion-panel-header>
            <div>
              <v-icon>mdi-account</v-icon>
              <span class="small-text">{{ item.name }}</span>
            </div>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <p>Altura: {{ item.height }}</p>
            <p>Cor do cabelo: {{ item.hair_color }}</p>
            <p>Cor dos olhos: {{ item.eye_color }}</p>
            <v-dialog
              v-model="dialog"
              width="500"
            >
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    v-bind="attrs"
                    v-on="on"
                  >
                  Mais informações
                  </v-btn>
                </template>
                <v-card>
                  <v-list>
                    <v-subheader>{{ item.name }}</v-subheader>
                      <v-list-item>Altura: {{ item.height }}</v-list-item>
                      <v-list-item>Peso: {{ item.mass }}</v-list-item>
                      <v-list-item>Cor da pele: {{ item.skin_color }}</v-list-item>
                      <v-list-item>Cor do cabelo: {{ item.hair_color }}</v-list-item>
                      <v-list-item>Cor dos olhos: {{ item.eye_color }}</v-list-item>
                      <v-list-item>Aniversário: {{ item.birth_year }}</v-list-item>
                      <v-list-item>Gênero: {{ item.gender }}</v-list-item>
                  </v-list>
                </v-card>
              </v-dialog>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-list>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      heros: [],
      page: 1,
      dialog: false
    };
  },
  async asyncData({ $axios }) {
    const heros = await $axios.$get(`people`);
    return { heros };
  },
};
</script>