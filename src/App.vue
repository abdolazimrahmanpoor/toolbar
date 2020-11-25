<template>
  <v-app>
      <v-row>
        <v-col cols="2">
 
               <Toolbar/>
             
        </v-col>

         <v-col>
   
        </v-col>
      </v-row>
  
  
  </v-app>
</template>

<script>
import Toolbar from './components/Toolbar';

export default {
  name: 'App',

  components: {
    Toolbar,
  },

  data: () => ({
     
  }),
};
</script>


