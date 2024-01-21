<template>
  <svg ref="svgRef"/>
</template>
<script>
import {onMounted, onUpdated, ref} from "vue";
import {Transformer} from 'markmap-lib';
import {Markmap} from 'markmap-view';

const transformer = new Transformer();
const initValue = `
# architecture
- <img src="https://variwiki.com/images/a/a1/Docker.png" width="100" height="80"/>
  docker
  - dockerfile
    - FROM
    - WORKDIR
    - COPY
    - ENV
    - RUN
    - CMD
    - EXPOSE
  - docker-compose
    - services
    - image
    - ports
    - volumes
    - environment
- <img src="https://upload.wikimedia.org/wikipedia/commons/0/00/Kubernetes_%28container_engine%29.png" width="100" height="80">
  kubernetes
    - installation
    - master node
      - kubectl
      - etcd
    - worker node
      - deployment
      - service
      - pods
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