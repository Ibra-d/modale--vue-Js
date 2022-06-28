<template>
  <body>
    <main>
      <p class="text_presentation">
        Les fenêtres modales sont des fenêtres qui apparaissent directement à
        l'intérieur de la fenêtre courante du navigateur, au-dessus de la page
        web qui les appelle. Il s'agit de fenêtres modales, c'est-à-dire de
        fenêtres qui prennent le contrôle de la page courante tant qu'elles sont
        affichées à l'écran.
      </p>
      <input
        type="button"
        value="Open modale"
        class="button_modale"
        @click="openModale"
      />
    </main>
    <section class="section">
      <p>
        La création de fenêtres modales (ou pas du reste) a toujours été un
        besoin récurrent des développeurs Web. Certes, il existe les méthodes
        natives de JavaScript alert(), prompt() ou confirm(), mais leur côté
        intrusif et surtout peu configurable les rend quasiment obsolètes.
      </p>
      <input
        type="button"
        value="X"
        class="close_modale"
        @click="closeModale"
      />
    </section>
  </body>
</template>

<script>
export default {
  data() {
    return {
      section: "",
    };
  },
  methods: {
    openModale() {
      this.section = document.querySelector(".section").classList.add("modale");
      this.section = document
        .querySelector(".section")
        .classList.remove("disp");
    },
    closeModale() {
      this.section = document.querySelector(".section").classList.add("disp");
      setTimeout(function () {
        this.section = document
          .querySelector(".section")
          .classList.remove("modale");
      }, 1000);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
body {
  position: relative;
  font-family: "Trebuchet MS", sans-serif;
  height: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: antiquewhite;
}
main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: justify;
}
main p {
  width: 30rem;
  padding: 1rem;
  border-radius: 1rem;
  font-size: large;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}
main input {
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;
  font-family: Monospace;
  height: 2.4rem;
  border-radius: 0.4rem;
  border: none;
  cursor: pointer;
  transition: 0.3s;
  background-color: rgb(182, 182, 250);
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}
main input:hover {
  background-color: rgb(126, 174, 255);
}
section {
  display: none;
  position: absolute;
  width: 30rem;
  padding: 1rem;
  border-radius: 1rem;
  font-size: large;
  background-color: #fff;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}
.modale {
  display: block;
  animation: slide 1s cubic-bezier(1, 0, 0, 1);
}
.disp {
  animation: slider 1s cubic-bezier(1, 0, 0, 1);
}
@keyframes slider {
  0% {
    transform: translateY(0rem);
  }
  100% {
    opacity: 0;
    transform: translateY(2rem);
  }
}
@keyframes slide {
  0% {
    transform: translateY(2rem);
    opacity: 0;
  }
  100% {
    transform: translateY(0rem);
  }
}
section input {
  position: absolute;
  top: -1rem;
  right: -1rem;
  height: 2.5rem;
  width: 2.5rem;
  border-radius: 50%;
  border: none;
  transition: 0.3s;
  color: red;
}
section input:hover {
  background-color: red;
  color: black;
  cursor: pointer;
}
</style>
