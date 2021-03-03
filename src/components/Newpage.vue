<template>
  <div class="me">
    <h1 class="purple--text mx-5 my-5">Me!</h1> 
    <v-container class="mx-3 my-3"> 
    <v-card max-width="375" class="mx-auto" >
    <v-img  src="image.jpg" height="300px" dark >
      <v-row class="fill-height">
        <v-card-title>
          <v-btn dark icon>
            <v-icon>mdi-chevron-left</v-icon>
          </v-btn>
          <v-spacer></v-spacer>
          <v-btn dark icon class="mr-4">
            <v-icon>mdi-pencil</v-icon>
          </v-btn>
          <v-btn dark icon>
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </v-card-title>
        <v-spacer></v-spacer>

        <v-card-title class="white--text pl-12 pt-12">
          <div class="display-1 pl-12 pt-12 purple--text">
            Negin Negin
          </div>
        </v-card-title>
      </v-row>
    </v-img>

    <v-list two-line>
      <v-list-item>
        <v-list-item-icon>
          <v-icon color="blue">
            mdi-phone
          </v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>(650) 555-1234</v-list-item-title>
        </v-list-item-content>

        <v-list-item-icon>
          <v-icon color="blue">mdi-message-text</v-icon>
        </v-list-item-icon>
      </v-list-item>

      <v-divider inset></v-divider>

      <v-list-item>
        <v-list-item-icon>
          <v-icon color="blue">
            mdi-email
          </v-icon>
        </v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title>example@gmail.com</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider inset></v-divider>

      <v-list-item>
        <v-list-item-icon>
          <v-icon color="blue"> mdi-map-marker</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-subtitle>Iran, Kerman</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-card>
           
    </v-container>
  </div>
 
</template>
<style>
.me{
  border:2px solid purple;
}

</style>



