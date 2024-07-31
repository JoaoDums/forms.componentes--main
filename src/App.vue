<script setup>
import { ref, reactive } from 'vue'
import EnvioForm from '@/components/EnvioForm.vue'
import FormsCria from '@/components/FormsCria.vue'

const form = reactive({
  nome: '',
  email: '',
  senha: '',
  confirmacao: '',
  data: '',
  endereco: '',
  cidade: '',
  estado: [],
  hobbies: '',
  lingprog: '',
  bio: ''
})
const save = ref(false)

function adicionar(dados) {
  Object.assign(form, dados)
  console.log(form)
  if (form.nome === '' || form.email === '' || form.senha == '') {
    alert('Os campos nome, e-mail e senha são obrigatórios')
  } else if (form.senha != form.confirmacao) {
    alert('Os campos senha e confirmação de senha não correspondem')
  } else {
    save.value = !save.value
  }
}
</script>

<template>
  <h1>FORMS CRIA</h1>
  <div class="flex-container">
    <FormsCria class="flex-item" @adicionar="adicionar" />
    <EnvioForm class="flex-item" v-if="save" :form="form" @adicionar="adicionar" />
  </div>
</template>

