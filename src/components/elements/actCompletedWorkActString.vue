<template>
  <tr>
    <td class="index">{{ index+1 }}</td>
    <td class="name"><a-input v-model="data.name" type="text"/></td>
    <td class="unit"><a-input v-model="data.unit" type="text"/></td>
    <td class="price"><a-input v-model="data.price" type="numeric" step="0.01"/></td>
    <td class="quantity"><a-input v-model="data.quantity"  type="numeric" step="0.01"/></td>
    <td class="sum">{{ formatter(data.price * data.quantity) }}</td>
    <td class="rubbish_container" @click="deleteString">
      <svg viewBox="-47 1 511 511.999" xmlns="http://www.w3.org/2000/svg"><path d="m209.140625 186c-8.28125 0-15 6.714844-15 15v235c0 8.285156 6.71875 15 15 15 8.285156 0 15-6.714844 15-15v-235c0-8.285156-6.714844-15-15-15zm0 0"/><path d="m279.78125 186.015625c-8.257812-.386719-15.273438 6.070313-15.625 14.347656l-10 235c-.355469 8.277344 6.070312 15.269531 14.347656 15.625.21875.007813.433594.011719.648438.011719 7.992187 0 14.632812-6.300781 14.976562-14.359375l10-235c.351563-8.28125-6.074218-15.273437-14.347656-15.625zm0 0"/><path d="m138.503906 186.015625c-8.277344.351563-14.699218 7.347656-14.347656 15.621094l10 235c.34375 8.0625 6.984375 14.363281 14.972656 14.363281.214844 0 .433594-.003906.652344-.015625 8.273438-.351563 14.699219-7.347656 14.347656-15.621094l-10-235c-.351562-8.277343-7.328125-14.726562-15.625-14.347656zm0 0"/><path d="m402.417969 185.136719h-34.164063l1.726563-29.398438h12.054687c8.28125 0 15-6.714843 15-15v-32.867187c0-24.8125-20.1875-45-45-45h-49.828125v-7.871094c0-30.328125-24.675781-55-55-55h-76.128906c-30.328125 0-55 24.671875-55 55v7.867188h-49.828125c-24.8125 0-45 20.1875-45 45v32.871093c0 8.285157 6.714844 15 15 15h12.050781l1.730469 29.398438h-34.53125c-8.285156 0-15 6.714843-15 15 0 8.28125 6.714844 15 15 15h36.296875l16.632813 282.742187c.464843 7.929688 7.03125 14.121094 14.972656 14.121094h251.480468c7.941407 0 14.507813-6.191406 14.972657-14.121094l16.632812-282.742187h35.929688c8.285156 0 15-6.71875 15-15 0-8.285157-6.714844-15-15-15zm-256.339844-130.136719c0-13.785156 11.214844-25 25-25h76.125c13.785156 0 25 11.214844 25 25v7.867188h-126.125zm-94.828125 52.867188c0-8.269532 6.730469-15 15-15h285.78125c8.273438 0 15 6.730468 15 15v17.871093h-315.78125zm269.488281 374.132812h-223.191406l-19.191406-326.261719h261.574219zm0 0"/></svg>
    </td>
  </tr>
</template>

<script>
export default {
  props: ['data', 'index'],
  methods: {
    deleteString: function () {
      this.$root.$emit('deleteElement', this.$props.index);
    }
  }
}
</script>

<style scoped lang="scss">
tr{
  &:hover{
    & td{
      background: #fff5ee;

      & input{
        //background: #fff5ee;
      }
    }
  }

  & td {
    border: 1px solid #eee;
    font-size: 14px;
    padding: 10px;
    & input{
      border-radius: 0;
      border: 0 solid;
    }

    &.index{
      width: 5%
    }
    &.name{
      width: 40%;
      padding: 0
    }
    &.unit{
      width: calc(10% - 20px);
      padding: 0
    }
    &.price{
      width: 15%;
      padding: 0
    }
    &.quantity{
      width: 5%;
      padding: 0
    }
    &.sum{
      width: 15%
    }

  }
}
.rubbish_container{
  width: 20px;
  padding: 5px 25px;
  cursor: pointer;
  & svg{
    height: 17px;
    width: 17px;
    margin: auto;
  }
}
</style>