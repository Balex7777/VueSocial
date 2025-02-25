<template>
<div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Войдите в аккаунт
            </v-card-title>

            <v-text-field
                label="Введите логин"
                v-model="login"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите пароль"
                v-model="password"
                outlined
            ></v-text-field>

            <v-btn @click="authenticate">
                Войти
            </v-btn>
        </v-card>
    </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
    };
  },
  methods: {
    authenticate() {
      this.axios
        .get(
          `https://37.77.104.246/api/jsonstorage/?id=69f756530dfb7a35cb40936791601741`
        )
        .then((response) => {
          let users = response.data;
          let found = false;
          for(let index in users){
              if(this.login == users[index].login && this.password == users[index].password){
                  this.$router.push('user/' + users[index].id);
                  this.$store.state.userData.id = users[index].id;
                  found = true;
                  break;
              }
          }
          if(!found){
              window.alert('неверный логин или пароль');
          }
        });
    },
  }
  
};
</script>
