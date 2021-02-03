<template>
<v-app id="app">
  <v-navigation-drawer
      color="green"
      dark
      expand-on-hover
      hide-overlay
      permanent
      right
      app
    >
    <v-list
      nav 
      shaped
      dense
    ><v-list-item-group>
        <v-list-item two-line>
          <v-list-item-avatar>
            <img :src="'https://randomuser.me/api/portraits/men/1.jpg'">
          </v-list-item-avatar>
          <v-list-item-content class="text-left">
            <v-list-item-title class="front-weight-black">SocialLink</v-list-item-title>
            <v-list-item-subtitle>Зубенко Михаил</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-divider class="my-3"/>
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-home-outline</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="text-left">Главная</v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account-outline</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="text-left">Мой профиль</v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account-multiple-plus-outline</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="text-left">Найти друзей</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
    </v-list>
    </v-navigation-drawer>
    <v-content class="px-12 py-3"> 
        <v-row class="text-left my-5">
            <v-col cols="10">
                <h1 class="green--text text--darken-2">
                    SocialLink
                </h1>
            </v-col>
        </v-row>
        <v-row class="text-left">
            <v-col cols="10">
                <h2 class="green--text text--darken-2">
                    Статья
                </h2>
            </v-col>
        </v-row>
        <v-row class="text-left">
            <v-col cols="4">
                <img src="https://c-masters.ru/storage/app/public/2020/05/17/62a15473cf9e801144e0d593fa4f094c5ead2864.jpg" style="max-width: 100%">
            </v-col>
            <v-col cols="6" class="text-left">
                <p>
                   Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus eum alias corporis at odio, aperiam odit labore sunt rem quaerat ipsum ipsa quod dolore unde vel architecto illum ullam consequuntur. ipsum dolor sit amet consectetur adipisicing elit. Quia ad doloribus ipsa velit nesciunt sit minus ullam eum. Iusto, natus omnis expedita laborum quam excepturi? Fuga exercitationem corporis voluptatem architecto.
                </p>
            </v-col>
        </v-row>
    </v-content>
</v-app>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
