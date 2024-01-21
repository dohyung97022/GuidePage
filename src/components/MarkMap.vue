<template>
  <svg ref="svgRef"/>
  <img alt="Vue logo" src="@/assets/logo.png">
</template>
<script>
import {onMounted, onUpdated, ref} from "vue";
import {Transformer} from 'markmap-lib';
import {Markmap} from 'markmap-view';

const transformer = new Transformer();
const initValue = `
# architecture
- <img src="https://miro.medium.com/v2/resize:fit:1200/1*XvJ0GDWOAEHNApZvw-dOVQ.png" width="100" height="80"/>
  docker
- <img src="@/assets/logo.png" width="100" height="80">
  kubernetes
`;

export default {
  name: 'App',
  setup() {
    const svgRef = ref();
    const value = ref(initValue);
    let mm;

    const update = () => {
      const {root} = transformer.transform(value.value);
      mm.setData(root);
      mm.fit();
    };

    onMounted(() => {
      mm = Markmap.create(svgRef.value);
      update();
    });
    onUpdated(update);
    return {
      svgRef,
      value,
    };
  },
};
</script>
<style scoped>

</style>