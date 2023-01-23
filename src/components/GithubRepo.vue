<template>
  <div>
    <v-row class="text-center">
      <v-col cols="6">
        <v-autocomplete
        v-model="user"
        label="Encontre seu usuário"
        :items="userlist"
        :loading="userloading"
        :search-input.sync="usersearch"
        item-text="login"
      />
      </v-col>
      <!-- <v-col cols="6">
        <v-select
          v-model="repo"
          :items="repolist"
          :loading="repoloading"
          item-text="name"
          label="Selecione o repositorio"
          return-object
          single-line
        ></v-select>
      </v-col> -->
    </v-row>
  </div>
</template>

<script>
  export default {
    data: () => ({
      user: null,
      usersearch: null,
      repolist: [],
      userlist: [],
    }),
    watch: {
      usersearch () {
          this.procuraUsuariosGithub()
      },
    }
  }
</script>
