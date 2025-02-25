<template>
  <div class="d-flex justify-center">
    <v-card width="600px" class="mt-12 pa-10">
      <v-card-title> Войдите в аккаунт </v-card-title>

      <v-text-field label="Введите логин" v-model="login" outlined></v-text-field>

      <v-text-field label="Введите пароль" v-model="password" outlined></v-text-field>

      <v-btn @click="authenticate"> Войти </v-btn>
    </v-card>
  </div>
</template>

<script>
import axios from "axios"; // Импорт Axios

export default {
  name: "Login",
  data() {
    return {
      login: "",
      password: "",
    };
  },
  methods: {
    async authenticate() {
      try {
        const response = await axios.get(
          `https://37.77.104.246/api/jsonstorage/?id=69f756530dfb7a35cb40936791601741`
        );

        let users = response.data;
        let found = false;

        for (let user of users) {
          if (this.login === user.login && this.password === user.password) {
            this.$router.push(`/user/${user.id}`);
            this.$store.state.userData.id = user.id;
            found = true;
            break;
          }
        }

        if (!found) {
          window.alert("Неверный логин или пароль");
        }
      } catch (error) {
        console.error("Ошибка при запросе данных:", error);
        window.alert("Ошибка сервера. Попробуйте позже.");
      }
    },
  },
};
</script>
