<template>
  <section>
    <div v-if="!show">
      <button @click="show = true">Add an Ipsum</button>
    </div>
    <div v-else>
      <h2>Add New Ipsum</h2>
      <IpsumForm class="form"
        :onAdd="handleAdd"
        :onCancel="() => show = false"/>
    </div>
  </section>
</template>

<script>
import IpsumForm from './IpsumForm';

export default {
  data() {
    return {
      show: false
    };
  },
  components: {
    IpsumForm
  },
  props: {
    ipsumTypes: Array,
    onAdd: Function
  },
  methods: {
    handleAdd(ipsum) {
      console.log('xyz');
      this.onAdd(ipsum);
      this.show = false;
    }
  }
};
</script>

<style>

</style>
