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

import {debouncerdecorator} from '@/helpers/debouncer.js'
  export default {
    data: () => ({
      user: null,
      usersearch: null,
      repolist: [],
      userlist: [],
      userloading: false,
    }),
    methods: {
      procuraUsuariosGithub: debouncerdecorator(function () { // atenção: não use ()=>{} aqui. vai quebrar o decorator
        console.log('faz de conta que eu perguntei pro github: ' + this.usersearch)
        this.userloading = true
        setTimeout(() => {
          this.userlist = [
            {login: 'joao'},
            {login: 'jose'}
          ]
          this.userloading = false
        }, 1000)
      }, 500)
    },
    watch: {
      usersearch () {
        this.userloading = true
        this.procuraUsuariosGithub()
      },
    }
  }
</script>
