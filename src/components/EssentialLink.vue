<template>
  <q-page>
    <div id="game-container">
      <div id="flashcard" v-if="!showResult">
        <p id="equation">{{ equation }}</p>
        <q-input v-model="answer" type="number" />
        <q-btn @click="check" label="Submit" />
      </div>
      <div id="result-screen" v-if="showResult">
        <p id="result" :style="{ color: color }">{{ msg }}</p>
        <q-btn @click="restart" label="Restart" />
      </div>
    </div>
  </q-page>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const equation = ref('');
    const answer = ref(null);
    const showResult = ref(false);
    const msg = ref('');
    const color = ref('');

    function generate() {
      let n1 = Math.floor(Math.random() * 1337) + 1;
      let n2 = Math.floor(Math.random() * 1337) + 1;
      let op = Math.random() < 0.5 ? '+' : '*';
      equation.value = `${n1} ${op} ${n2}`;
      answer.value = null;
    }

    function check() {
      let correct = eval(equation.value);

      if (answer.value === correct) {
        msg.value = 'Correct!';
        color.value = 'green';
      } else {
        msg.value = 'Incorrect!';
        color.value = 'red';
      }

      showResult.value = true;
    }

    function restart() {
      showResult.value = false;
      generate();
    }

    generate();

    return {
      equation,
      answer,
      showResult,
      msg,
      color,
      generate,
      check,
      restart,
    };
  },
};
</script>
