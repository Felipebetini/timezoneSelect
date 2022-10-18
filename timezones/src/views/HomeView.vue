<template>
  <div class="home bg-black">
    <ModalLocation></ModalLocation>
  </div>
</template>

<script>
// @ is an alias to /src
import ModalLocation from '../components/ModalLocation.vue';

export default {
  name: 'HomeView',
  components: {
    ModalLocation,
  },
};
</script>
