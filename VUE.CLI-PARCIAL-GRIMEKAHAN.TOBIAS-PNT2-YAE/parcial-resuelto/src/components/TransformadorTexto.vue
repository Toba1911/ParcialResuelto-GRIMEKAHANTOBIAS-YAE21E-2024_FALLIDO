<template>
  <div class="container">
    <form @submit.prevent>
      <div class="form-group">
        <label for="inputText">Ingrese texto:</label>
        <input type="text" id="inputText" class="form-control" v-model="inputText" />
      </div>
    </form>

    <div v-show="inputText" class="mt-4 animated fadeIn">
      <p>Codificado: {{ encodedText }}</p>
      <p>Todo en mayúscula: {{ uppercaseText }}</p>
      <p>Todo en minúscula: {{ lowercaseText }}</p>
      <p>Intercalado comenzando con mayúscula: {{ alternatingTextCapStart }}</p>
      <p>Intercalado comenzando con minúscula: {{ alternatingTextLowerStart }}</p>
      <p>Cantidad de caracteres: {{ charCount }}</p>
    </div>

    <hr class="my-4">

    <div class="mt-4 animated fadeIn">
      <p class="font-weight-bold">Respuestas:</p>
      <ul>
        <li>Pregunta 1/3: c</li>
        <li>Pregunta 2/3: c</li>
        <li>Pregunta 3/3: a</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: ''
    };
  },
  computed: {
    encodedText() {
      return this.encodeText(this.inputText.toLowerCase());
    },
    uppercaseText() {
      return this.inputText.toUpperCase();
    },
    lowercaseText() {
      return this.inputText.toLowerCase();
    },
    alternatingTextCapStart() {
      return this.alternatingCase(this.inputText, true);
    },
    alternatingTextLowerStart() {
      return this.alternatingCase(this.inputText, false);
    },
    charCount() {
      return this.inputText.length;
    }
  },
  methods: {
    alternatingCase(text, startWithUpperCase) {
      return text.split('').map((char, index) => {
        if ((index % 2 === 0 && startWithUpperCase) || (index % 2 !== 0 && !startWithUpperCase)) {
          return char.toUpperCase();
        } else {
          return char.toLowerCase();
        }
      }).join('');
    },
    encodeText(text) {
      const vowelMap = { 'a': 'u', 'e': 'o', 'i': 'i', 'o': 'e', 'u': 'a' };
      return text.split('').map(char => vowelMap[char] || char).join('');
    }
  }
};
</script>

<style scoped>
.animated {
  animation-duration: 3s;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.fadeIn {
  animation-name: fadeIn;
}

</style>
