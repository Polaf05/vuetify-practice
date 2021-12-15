<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
  <v-card
    height="400"
    width="256"
    class="mx-auto"
  >
   
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Kiven To Do
          </v-list-item-title>
          <v-list-item-subtitle>
            ang sarap
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    
  </v-card>
      <!--  -->
    </v-navigation-drawer>

       <v-app-bar app color="white" elevate-on-scroll scroll-target="#scrolling-techniques-7">
          
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

          <v-toolbar-title>To Do List</v-toolbar-title>

          <v-spacer></v-spacer>

          <v-btn icon>
            <v-icon>mdi-magnify</v-icon>
          </v-btn>

          <v-btn icon>
            <v-icon>mdi-heart</v-icon>
          </v-btn>

          <v-btn icon>
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </v-app-bar>
    

    <v-main>
      <!--  -->
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>


  export default {

    components:{

    },
    data: () => ({ 
        drawer: null, 
        items: [
          { title: 'To do list', icon: 'mdi-checkbox-marked-circle-plus-outline', to:'/' },
          { title: 'About', icon: 'mdi-help-box', to:'/about' },
          { title: 'Axies', icon: 'mdi-fish', to:'/axie'}
        ],
        
     }),
    
  }
</script>