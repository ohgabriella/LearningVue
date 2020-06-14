<template>
  <div id="app">
    <h1>Formulário Desafio</h1>
    <div class="conteudo">
      <form class="painel">
        <div class="cabecalho">Formulário</div>
        <!-- Exercicio 01 -->
        <!-- Criar uma formulário de registro -->
        <!-- Nome completo (Nome e Sobrenome) -->
        <!-- Email -->
        <!-- Senha -->
        <!-- Armazenar Dados? (Sim/Não) -->
        <Rotulo nome="Nome completo">
          <input type="text" v-model="nomeCompleto" />
        </Rotulo>
        <Rotulo nome="E-mail">
          <input type="text" v-model="email" />
        </Rotulo>
        <Rotulo nome="Senha">
          <input type="password" v-model="senha" />
        </Rotulo>
        <Rotulo nome="Armazenar dados?">
          <span>
            <input type="radio" value="sim" v-model="dado" />Sim
          </span>
          <span>
            <input type="radio" value="nao" v-model="dado" />Não
          </span>
        </Rotulo>
        <button @click.prevent="salvar">Enviar</button>
      </form>

      <!-- Exercicio 02 -->
      <!-- Só mostrar o fomulário de não tiver sido submetido -->
      <!-- Mostrar a área de Resultado apenas quando o formulário for submetido -->
      <div class="painel">
        <div class="cabecalho">Resultado</div>
        <Rotulo nome="Nome completo">
          <span>{{ nomeCompleto }}</span>
        </Rotulo>
        <Rotulo nome="E-mail">
          <span>{{ email }}</span>
        </Rotulo>
        <Rotulo nome="Senha">
          <span>{{ senha }}</span>
        </Rotulo>
        <Rotulo nome="Armazenar dados?">
          <span>{{ dado }} - salvo = {{ salvo }}</span>
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

export default {
  name: "app",
  components: { Rotulo },
  data() {
    return {
      nomeCompleto: "",
      email: "",
      senha: "",
	  dado: "sim",
	  salvo: false
    };
  },
  methods: {
    salvar() { return this.salvo = true; }
  }
};
</script>

<style>
body {
  background-color: #ececec;
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
  background-color: #ddd;
  padding: 10px 0px;
  border-radius: 5px;
  font-size: 1.4rem;
}

#app form button {
  float: right;
  margin: 10px 0px;
  padding: 10px 20px;
  font-size: 1.4rem;
  border-radius: 5px;
  color: #fff;
  background-color: #2196f3;
}

#app h1 {
  font-weight: 200;
  margin: 20px;
  padding: 0;
}

.mr-4 {
  margin-right: 40px;
}
</style>
