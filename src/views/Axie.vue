<template>
<div>
     <v-btn-toggle
        v-model="icon"
        borderless
      >
        <v-btn v-for="axie in axies" :key="axie.class" @click="send(axie)">
          <span class="hidden-sm-and-down">{{axie.class}}</span>

          <v-icon right>
            mdi-fish
          </v-icon>

        </v-btn>

      </v-btn-toggle>

      <Spes v-bind:axie = current />

       

</div>
</template>

<script>
import Spes from './SpecificAxie.vue'

export default ({
    components:{

        Spes

    },
    data() {
        return{
        axies:[
          { class: 'Dusk', speed: '48', skill: '35', health:'52', morale: '42' , name:'Disablo', mouth:'Tiny Turtle', horn:'Kestrel',back:'Green Thorns',tail:'Hot Butt', img:'../assets/dusk.jpg'},
          { class: 'Bug', speed: '34', skill: '35', health:'48', morale: '55', name:'Bugsy Boy', mouth:'Pincer', horn:'Parasite',back:'Cupid',tail:'Fish Snack', img:'../assets/bug.jpg'},
          { class: 'Plant', speed: '32', skill: '35', health:'59', morale: '48', name:'Pocky ng ina mo', mouth:'Serious', horn:'Pocky',back:'Pumpkin',tail:'Hot Butt',  img:'../assets/plant.jpg'},
        ],
        current:'',
        }
        
    },
    methods: {
        send(axie)
        {
            this.current = axie;
        }
    }
})
</script>
