<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>密码生成器</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn 
      icon
      href="https://github.com/sersoong/nuxt-password-gen"
      target="_blank"
      >
        <v-icon>fab fa-github</v-icon>
      </v-btn>
    </v-toolbar>
    
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
   name:"default"
  }
</script>
