
<template>
  <div>
    <IpsumDetail
     v-if="selected"
     :ipsum="selected"/>
    <ul>
        <AddIpsum
        :onAdd="handleAdd"/>
        <IpsumList
        :onSelect="handleSelect"
        :ipsums="ipsums"/>
    </ul>
  </div>
</template>

<script>
import ipsumsApi from '../services/IpsumApi.js';
import IpsumDetail from './IpsumDetail.vue';
import IpsumList from './IpsumList.vue';
import AddIpsum from './AddIpsum.vue';

export default {
  data() {
    return {
      ipsums: ipsumsApi.getAll(),
      selected: null,
    };
  },
  components:{
    IpsumDetail,
    IpsumList,
    AddIpsum
    
  },
  methods: {
    handleSelect(ipsum) {
      this.selected = ipsum;
    },
    handleAdd(ipsum) {
      console.log('banana', this.ipsums);
      this.ipsums.push(ipsum);
      this.handleSelect(ipsum);
    }
  }
};

</script>

<style>
