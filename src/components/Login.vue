<template>
  <v-app>
    <div class="hello">
      <form
        id="register"
        @submit.prevent="checkForm"
        action="https://vuejs.org/"
        method="post"
      >
        <div class="container">
          <h2>Entrar</h2>
          <br />
          <label for="email">E-mail:</label>
          <input
            v-model="form.mail"
            type="email"
            id="mail"
            name="mail"
            placeholder="Ex: nome@gmail.com"
            required="true"
          />

          <label for="password">Senha:</label>
          <input
            v-model="form.pass"
            type="password"
            id="pass"
            name="pass"
            placeholder=""
            required="true"
            @change="validatePassword($event)"
          />

          <v-btn
            color="primary"
            class="mx-auto black--text"
            large
            type="submit"
            @click="redirect"
          >
            Entrar
          </v-btn>
        </div>
      </form>
    </div>
  </v-app>
</template>

<script>
export default {
  name: "RegistrationForm",
  data: function () {
    return {
      form: {
        mail: null,
        pass: null,
      },
    };
  },
  methods: {
    redirect: function () {
      if (this.form.mail === "admin@gmail.com" && this.form.pass === "admin") {
        console.log("ADMIN");
        window.location.href = "/estoque";
        return;
      } else if (this.form.mail === "user@gmail.com" && this.form.pass === "user") {
        window.location.href = "/";
        console.log("USER");
        return;
      }

      console.log("ERRO");
      alert("Usuário não cadastrado ou dados incorretos. Por favor, tente novamente.")
    },
  },
};
</script>

<style scoped>
form {
  width: 500px;
  margin: 0 auto;
}

.container {
  padding: 10px;
}

h2 {
  text-align: center;
}

label {
  display: block;
  font-size: 1.3em;
}

input[type="text"],
input[type="email"],
input[type="password"] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  border: none;
  background: #f1f1f1;
}

input[type="text"]:focus,
input[type="email"]:focus,
input[type="password"]:focus {
  background-color: #ddd;
  outline: none;
}

::placeholder {
  color: #A5A8A9;
}

:-ms-input-placeholder {
  /* Internet Explorer 10-11 */
  color: red;
}

::-ms-input-placeholder {
  /* Microsoft Edge */
  color: red;
}
</style>
