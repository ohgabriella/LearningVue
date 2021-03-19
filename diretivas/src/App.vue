<template>
  <div id="app">
    <h1>Diretivas (Desafio)</h1>
    <hr />
    <!-- Exercício -->
    <!-- Escreva uma diretiva que funcione com o v-on (escute eventos) -->
    <button v-quando:atrasar="{cor: 'green', text: 'Gabriella', texto}">Vou mudar de cor</button>

    <button v-quando:click="texto">Clique aqui</button>

    <button v-quando:click="mensagem">{{text}}</button>

    <p v-quando:mouseenter="mouseEnter" v-quando:mouseleave="mouseLeave">Teste de mouse event</p>

    <p></p>
  </div>
</template>

<script>
export default {
  directives: {
    quando: {
      bind(el, binding, vnode) {
        const tipo = binding.arg;
        const fn = binding.value;
        el.addEventListener(tipo, fn);

        // const mudarTexto = texto => {
        //   if (binding.arg === "click") {
        // 	binding.value.text = texto;
        // 	console.log(binding.value.text);

        //   }
        // };

        let atraso = 0;
        if (binding.modifiers["atrasar"]) atraso = 3000;

        setTimeout(() => {
          el.style.backgroundColor = binding.value.cor;
        }, atraso);
      }
    }
  },
  data() {
    return {
      text: "Gabriella"
    };
  },
  methods: {
    texto() {
      alert("Clicou!!");
    },
    mouseEnter() {
      alert("Isso ae!!");
    },
    mouseLeave() {
      console.log("O mouse foi deixado");
    },
    mensagem() {
      this.text = "Clicado";
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 2.5rem;
}

button {
  width: 350px;
  margin: 10px auto;
  padding: 10px 20px;
  font-size: 1.4rem;
  border-radius: 10px;
  color: #fff;
  background-color: lightseagreen;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
