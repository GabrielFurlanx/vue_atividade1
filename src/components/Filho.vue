<template>
  <div>
    <div>
      <p>Nome: <input type="text" v-model="novoFilho.nome" placeholder="Digite o nome" /></p>
    </div>
    <div>
      <p>Idade: <input type="number" v-model="novoFilho.idade" placeholder="Digite a idade" /></p>
    </div>
    <div>
      <p>Gênero:</p>
      <label>
        <input type="radio" v-model="novoFilho.genero" value="masculino" /> Masculino
      </label>
      <label>
        <input type="radio" v-model="novoFilho.genero" value="feminino" /> Feminino
      </label>
    </div>
    <div>
      <p>Inteligência: <input type="text" v-model="novoFilho.inteligencia" placeholder="Digite a inteligência" /></p>
    </div>

    <button @click="criarFilho">Criar Filho</button>
    <button @click="excluirFilho(index)">Excluir Filho</button>

    <hr />

    <div v-if="filhos.length">
      <h2>Lista de Filhos Criados</h2>
      <div v-for="(filho, index) in filhos" :key="index">
        <p><strong>Filho {{ index + 1 }}:</strong></p>
        <p>Nome: {{ filho.nome }}</p>
        <p>Idade: {{ filho.idade }}</p>
        <p>Gênero: {{ filho.genero }}</p>
        <p>Inteligência: {{ filho.inteligencia }}</p>
        <hr />
      </div>
    </div>
    <div v-else>
      <p>A lista está vazia.</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const novoFilho = ref({
  nome: "",
  idade: null,
  genero: "",
  inteligencia: ""
})

const filhos = ref([])

const criarFilho = () => {
  filhos.value.push({ ...novoFilho.value })
  novoFilho.value.nome = ""
  novoFilho.value.idade = null
  novoFilho.value.genero = ""
  novoFilho.value.inteligencia = ""
}

const excluirFilho = (index) => {
  filhos.value.splice(index, 1)
}
</script>
