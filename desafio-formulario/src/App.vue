<template>
  <div id="app">
    <h1>Formulário Desafio</h1>
    <div class="conteudo">
      <form class="painel" v-if="!enviado">
        <div class="cabecalho">Formulário</div>
        <!-- Exercicio 01 -->
        <!-- Criar uma formulário de registro -->
        <!-- Nome completo (Nome e Sobrenome) -->
        <!-- Email -->
        <!-- Senha -->
        <!-- Armazenar Dados? (Sim/Não) -->
        
        <NomeCompleto v-model="nomeCompleto"></NomeCompleto>

        <Rotulo nome="E-mail">
          <input type="text" v-model="email" />
        </Rotulo>
        <Rotulo nome="Senha">
          <input type="password" v-model="senha" />
        </Rotulo>
        <Rotulo nome="Armazenar dados">
          <span>
            <input class="mr-4" type="checkbox" v-model="salvo" @click="!salvo" />Sim
          </span>
        </Rotulo>
        <button @click.prevent="salvar">Enviar</button>
      </form>

      <!-- Exercicio 02 -->
      <!-- Só mostrar o fomulário de não tiver sido submetido -->
      <!-- Mostrar a área de Resultado apenas quando o formulário for submetido -->
      <div class="painel" v-else>
        <div class="cabecalho">Resultado</div>
        <Rotulo nome="Nome completo">
          <span>{{ nomeCompleto.nome }} {{ nomeCompleto.sobrenome }}</span>
        </Rotulo>
        <Rotulo nome="E-mail">
          <span>{{ email }}</span>
        </Rotulo>
        <Rotulo nome="Senha">
          <span>{{ senha }}</span>
        </Rotulo>
        <Rotulo nome="Armazenar dados?">
          <span>{{ salvo }}</span>
        </Rotulo>
      </div>

      <!-- Exercicio 03 -->
      <!-- Crie um componente personalizado NomeCompleto -->
      <!-- Esse componente deve receber Nome e Sobrenome -->
    </div>
  </div>
</template>

<script>
import Rotulo from "./components/Rotulo.vue";
import NomeCompleto from "./components/NomeCompleto.vue";

export default {
  name: "app",
  components: { Rotulo, NomeCompleto },
  data() {
    return {
      nomeCompleto: {
        nome: "",
        sobrenome: ""
      },
      email: "",
      senha: "",
      salvo: false,
      enviado: false
    };
  },
  methods: {
    salvar() {
      return (this.enviado = true);
    }
  }
};
</script>

<style>
body {
  background-color: cadetblue;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  display: flex;
  flex-direction: column;
}

.conteudo {
  display: flex;
}

.painel {
  flex: 1;
  background: #fff;
  margin: 0px 10px;
  padding: 20px;
  border: 1px solid #aaa;
  border-radius: 5px;
}

.painel .cabecalho {
  width: 100%;
  background-color: darksalmon;
  padding: 10px 0px;
  border-radius: 5px;
  font-size: 1.4rem;
}

#app form button {
  float: right;
  margin: 10px 0px;
  padding: 10px 20px;
  font-size: 1.2rem;
  border-radius: 5px;
  background-color: darksalmon;
  border-color: darksalmon;
}

#app h1 {
  font-weight: 200;
  margin: 20px;
  padding: 0;
}

.mr-4 {
  margin-right: 20px;
}
</style>
