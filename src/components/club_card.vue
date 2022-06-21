<template>
  <v-card
      max-width="444"
      height="100%"
  >
    <v-carousel hide-delimiter-background
                height="200">
      <v-carousel-item v-for="picture in club.pictures" :key="picture">

        <v-img height="200"
               :src="'http://85.193.83.204:8000' + picture.image"
               cover>
          <v-row
              class="fill-height"
              justify="center"
          >
          </v-row>
        </v-img>
      </v-carousel-item>
    </v-carousel>
    <v-card-title>
      {{club.name}}
    </v-card-title>
    <v-card-subtitle class="pt-4">
      {{ teacher }}
    </v-card-subtitle>

    <v-card-text >
      <div>{{ club.description }}</div>
      <br>
      <div><em>{{ club.price }} руб. в месяц</em></div>
    </v-card-text>

    <v-card-actions>
      <v-btn color="orange">
        ПОДРОБНЕЕ
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "club_card",
  props: ['club'],
  computed: {
    teacher() {
      console.log(this.club)
      for (const attribute of this.club.attributes) {
        if (attribute.attribute.name === "Преподаватель") {
          return attribute.value
        }
      }
      return ""
    }
  }
}
</script>

<style scoped>

</style>