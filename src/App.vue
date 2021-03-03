<template>
  <v-app > 
      <v-content class="mx-5 my-5">
        <router-view><Newpage /></router-view>
      </v-content>
  </v-app>
</template> 

<script>
import Newpage from '@/components/Newpage'


export default {
  name: 'App',
  components:{ 
  Newpage },

  data: () => ({
    //
  }),
};
</script>
