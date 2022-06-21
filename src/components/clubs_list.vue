<template>
  <v-container>
    <v-row justify="start" align="stretch">
      <template v-for="(club, index) in clubs" :key="club.id">
        <v-col>
          <Club_card :club="club"></Club_card>
        </v-col>
        <v-responsive
            v-if="index + 1 % 4 === 0"
            :key="`width-${index}`"
            width="100%"
        ></v-responsive>
      </template>
    </v-row>
  </v-container>
</template>

<script>
import Club_card from "@/components/club_card";

export default {
  name: "clubs_list",
  components: {Club_card},
  props: ["clubs"]
}
</script>

<style scoped>

</style>