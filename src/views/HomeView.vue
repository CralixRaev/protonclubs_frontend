<template>
  <div class="home">
    <v-navigation-drawer app>
      <v-card
          flat
          color="transparent"
      >
        <v-card-text>
          <v-row>
            <v-col class="px-4">
              <v-range-slider
                  v-model="price_range"
                  :max="max"
                  :min="min"
                  hide-details
                  class="align-center"
              >
              </v-range-slider>
            </v-col>
          </v-row>
          <v-row>
            <v-col>
              <v-text-field
                  :value="price_range[0]"
                  class="mt-0 pt-0"
                  type="number"
                  label="От"
                  @change="$set(price_range, 0, $event)"
              ></v-text-field>
            </v-col>
            <v-col>
              <v-text-field
                  :value="price_range[1]"
                  class="mt-0 pt-0"
                  type="number"
                  label="До"
                  @change="$set(price_range, 1, $event)"
              ></v-text-field>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-navigation-drawer>
    <Suspense>
      <template #default>
        <Club_list :clubs="clubs"/>
      </template>
      <template #fallback>
        Loading...
      </template>
    </Suspense>
  </div>
</template>

<script>
// @ is an alias to /src
import Club_list from '@/components/clubs_list.vue'
import axios from "axios";

export default {
  name: 'HomeView',
  data() {
    return {
      price_range: [0, 1200],
      min: 0,
      max: 1230000
    }
  },
  components: {
    Club_list
  },
  async setup() {
    const response = await axios.get('http://85.193.83.204/clubs/')
    const clubs = response.data
    return {
      clubs
    }
  }
}
</script>
