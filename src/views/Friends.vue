<template>
<div>

    <h2 class="my-8">Друзья</h2>

    <v-row v-for="(user, i) in users" v-bind:key="i">
        <v-col sm="8">
            <v-card>
              <v-card-title>
                <v-card-actions>
                    <v-list-item class="grow">
                    <v-list-item-avatar color="grey darken-3" size="80">
                        <v-img
                        class="elevation-6"
                        alt=""
                        :src="`https://randomuser.me/api/portraits/men/${i + 1}.jpg`"
                        ></v-img>
                    </v-list-item-avatar>
                    </v-list-item>
                </v-card-actions>
                <v-divider
                class="mx-4"
                vertical
                ></v-divider>
                <div>
                    <v-item>
                        <span class="font-weight-bold headline">{{user.name}}</span>
                    </v-item><br>
                    <v-item>
                        <div class="title headline grey--text">{{user.username}}</div>
                    </v-item>
                    <div class="pa-2">
                        <v-btn
                        color="success"
                        dark
                        right
                        link :to="`/user/${i + 1}`"> 
                        <v-list-item-icon>
                            <v-icon>mdi-card-account-details-outline</v-icon>
                        </v-list-item-icon>
                        
                        
                        Перейти в профиль
                        </v-btn>
                    </div>
                </div>
              </v-card-title>
              
            </v-card>
        </v-col>
    </v-row>

  </div>
</template>

<script>
export default {
  name: "Friends",
  data() {
    return {
      userData: "",
      users: []
    };
  },
  methods: {
    getUserData() {
      this.axios
        .get(
          `http://jsonplaceholder.typicode.com/users/${this.$route.params.id}`
        )
        .then((response) => {
          this.userData = response.data;
        });
    },
    getUserPosts() {
      this.axios
        .get(
          `http://jsonplaceholder.typicode.com/users`
        )
        .then((response) => {
          this.users = response.data;
        });
    },
  },
  mounted() {
    this.getUserData();
    this.getUserPosts();
  },
  watch: {
    $route() {
      this.getUserData();
      this.getUserPosts();
    },
  },
};
</script>
