<template>
   <v-card>
    <v-list>
      <v-subheader>Planets Star Wars</v-subheader>
      <v-expansion-panels>
        <v-expansion-panel v-for="(item, i) in planet.results" :key="i">
          <v-expansion-panel-header>
            <div>
              <v-icon>mdi-account</v-icon>
              <span class="small-text">{{ item.name }}</span>
            </div>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <p>Rotation period: {{ item.rotation_period }}</p>
            <p>Orbital period: {{ item.orbital_period }}</p>
            <p>Diameter: {{ item.diameter }}</p>
            <p>Climate: {{ item.climate }}</p>
            <p>Gravity: {{ item.gravity }}</p>
            <p>Terrain: {{ item.terrain }}</p>
            <p>Surface water: {{ item.surface_water }}</p>
            <p>Population: {{ item.population }}</p>
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
      planet: []
    }
  },
  async asyncData({ $axios }) {
    const planet = await $axios.$get(`planets`);
    return { planet };
  }
}
</script>