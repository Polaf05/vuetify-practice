<template>
    <v-card
    class="mx-auto"
    max-width="344"
    outlined
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div class="text-overline mb-4">
          {{axie.class}}
        </div>
        <v-list-item-title class="text-h5 mb-1">
         {{axie.name}}
        </v-list-item-title>
        <v-list-item-subtitle>Health:{{axie.health}} Speed:{{axie.speed}} Skill:{{axie.skill}} Morale:{{axie.morale}}</v-list-item-subtitle>
        <v-list-item>Mouth : {{axie.mouth}}</v-list-item>
        <v-list-item>Horn : {{axie.horn}}</v-list-item>
        <v-list-item>Back : {{axie.back}}</v-list-item>
        <v-list-item>Tail : {{axie.tail}}</v-list-item>
        
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="80"
        color="grey"
      ><img
        :src="require('../assets/' + axie.class + '.jpg')"
      ></v-list-item-avatar>
    </v-list-item>
  </v-card>
</template>

<script>
export default ({

    props:['axie'],

    data() {
        
    },
})
</script>
