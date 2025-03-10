<template>
  <div class="calculatrice">
    <EcranCalculatrice :resultat="resultat" :leftOperator="leftOperator" :operation="operation" :rightOperator="rightOperator" />
    <div class="boutons">
      <BoutonCalculatrice v-for="btn in boutons" :key="btn" :value="btn" @send-value="handleButtonClick" />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import EcranCalculatrice from './EcranCalculatrice.vue';
import BoutonCalculatrice from './BoutonCalculatrice.vue';

export default {
  components: {
    EcranCalculatrice,
    BoutonCalculatrice,
  },
  setup() {
    const leftOperator = ref('');
    const rightOperator = ref('');
    const operation = ref('');
    const resultat = ref('0');
    
    const boutons = ['7', '8', '9', '+', '4', '5', '6', '-', '1', '2', '3', '*', 'C', '0', '=', '/'];

    const handleButtonClick = (value) => {
      if (!isNaN(value)) {
        if (operation.value) {
          rightOperator.value += value;
        } else {
          leftOperator.value += value;
        }
      } else if (['+', '-', '*', '/'].includes(value)) {
        if (leftOperator.value && !rightOperator.value) {
          operation.value = value;
        }
      } else if (value === '=') {
        if (leftOperator.value && rightOperator.value && operation.value) {
          const left = parseFloat(leftOperator.value);
          const right = parseFloat(rightOperator.value);
          if (operation.value === '/' && right === 0) {
            resultat.value = 'Erreur';
          } else {
            resultat.value = eval(`${left} ${operation.value} ${right}`);
          }
        }
      } else if (value === 'C') {
        leftOperator.value = '';
        rightOperator.value = '';
        operation.value = '';
        resultat.value = '0';
      }
    };

    return {
      leftOperator,
      rightOperator,
      operation,
      resultat,
      boutons,
      handleButtonClick,
    };
  },
};
</script>

<style scoped>
.calculatrice {
  width: 240px;
  padding: 15px;
  border: 2px solid #ff80bf;
  border-radius: 15px;
  background-color: #d9ffcc;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

.boutons {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.numbers {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}

.operations {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>