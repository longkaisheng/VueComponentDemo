<template>
  <div class="container">
      容器组件A
    <ContainerD/>
    <ViewComponent :priveAttr="priveAttr" :commonAttr="commonAttr" :containerBAttr="containerB.attr" @on-update="onUpdate"/>
  </div>
</template>
<script>
import { mapState, mapActions } from 'vuex';
import ViewComponent from './view.vue';
import ContainerD from './containerD/index.vue';

export default {
    props: {
        commonAttr: {
            type: String,
            default: ''
        }
    },
    data() {
        return {
            priveAttr: 'prive attr',
        }
    },
    mounted() {
        console.log(this.containerA);
        console.log(this.containerB);
        console.log(this.containerC);
        console.log(this.containerC.ContainerD);
    },
    computed: {
        ...mapState(['containerA', 'containerB', 'containerC'])
    },
    methods: {
        ...mapActions(['updateContainerB']),
        onUpdate() {
            this.updateContainerB();
        }
    },
    components: {
        ViewComponent,
        ContainerD
    }
}
</script>


