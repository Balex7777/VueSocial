<template>
<div>
    <v-row class="text-left">
      <v-col cols="10">
        <h1 class="green--text text--darken-2">
          <v-icon large color="green darken-2">mdi-account-outline</v-icon>
          {{userData.name}}
        </h1>
      </v-col>
    </v-row>
    <v-row class="text-left">
      <v-col cols="2">
        <img
          v-bind:src="`https://randomuser.me/api/portraits/men/${userId}.jpg`"
          style="max-width: 100%"
        />
      </v-col>
      <v-col cols="10" class="text-left">
        <p>
          Веб-сайт:
          <a :href="'https://' + userData.website" target="_blank">{{
            userData.website
          }}</a>
        </p>
        <p>
          E-mail: <a :href="'mailto:' + userData.email">{{ userData.email }}</a>
        </p>
        <p>Город: {{ userData.address.city }}</p>
        <p>Место работы: {{ userData.company.name }}</p>
      </v-col>
    </v-row>

    <v-divider></v-divider>

    <h2 class="my-8">Публикации</h2>

    <v-row v-for="(post, i) in posts" v-bind:key="i">
        <v-col sm="8">
            <v-card>
              <v-card-title>
                <v-icon large left> mdi-format-quote-open </v-icon>
                <span class="title font-weight-bold headline">{{post.title}}</span>
              </v-card-title>
        
              <v-card-text>
                "{{post.body}}"
              </v-card-text>
        
              <v-card-actions>
                <v-list-item class="grow">
                  <v-list-item-avatar color="grey darken-3">
                    <v-img
                      class="elevation-6"
                      alt=""
                      :src="`https://randomuser.me/api/portraits/men/${userId}.jpg`"
                    ></v-img>
                  </v-list-item-avatar>
        
                  <v-list-item-content>
                    <v-list-item-title>{{userData.name}}</v-list-item-title>
                  </v-list-item-content>
        
                  <v-row align="center" justify="end">
                    <v-icon class="mr-1"> mdi-heart </v-icon>
                    <span class="subheading mr-2">256</span>
                    <span class="mr-1">·</span>
                    <v-icon class="mr-1"> mdi-share-variant </v-icon>
                    <span class="subheading">45</span>
                  </v-row>
                </v-list-item>
              </v-card-actions>
            </v-card>
        </v-col>
    </v-row>

  </div>
</template>

<script>
export default {
  name: "About",
  data() {
    return {
      userData: "",
      userId: '',
      posts: []
    };
  },
  methods: {
    getUserData() {
      this.axios
        .get(
          `https://jsonplaceholder.typicode.com/users/${this.userId}`
        )
        .then((response) => {
          this.userData = response.data;
          this.$store.commit('setName', this.userData.name)
        });
    },
    getUserPosts() {
      this.axios
        .get(
          `https://jsonplaceholder.typicode.com/posts?userId=${this.userId}`
        )
        .then((response) => {
          this.posts = response.data;
          
        });
    },
  },
  mounted() {
    if(this.$router.currentRoute.path == "/")
      this.userId = this.$state.useId;
    else
      this.userId = this.$route.params.id;
    this.getUserData();
    this.getUserPosts();
    
  },
  watch: {
    $route() {
      if(this.$router.currentRoute.path == "/")
        this.userId = this.$state.useId;
      else
        this.userId = this.$route.params.id;
      this.getUserData();
      this.getUserPosts();
      
    },
  },
};
</script>
