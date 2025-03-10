<template>
  <div class="ecran">
    <p>{{ operation }}</p>
    <p>{{ resultat }}</p>
  </div>
</template>

<script>
import { computed } from 'vue';

export default {
  props: ['leftOperator', 'operation', 'rightOperator', 'resultat'],
  setup(props) {
    const operation = computed(() => `${props.leftOperator} ${props.operation} ${props.rightOperator}`);
    return { operation };
  }
};
</script>

<style scoped>
.ecran {
  background: #3a3838;
  color: #fff;
  padding: 15px;
  font-size: 22px;
  text-align: right;
  border-radius: 10px;
  margin-bottom: 15px;
  box-shadow: inset 0px 2px 4px rgba(0, 0, 0, 0.3);
}
</style>