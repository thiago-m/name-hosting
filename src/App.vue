<template>
  <div id="slogan">
    <div class="text-center">
      <h1>Name Hosting</h1>
      <h6 class="text-secondary">
        Gerador de nomes usando Vue.js Graphql e Node
      </h6>
      <br>
    </div>  
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <AppItemList name="Prefixos" :itens="prefixos" />
          </div>
          <div class="col-md">
            <AppItemList name="Sufixos" :itens="sufixes" />
          </div>
        </div>
        <br>
        <AppDomainsList :prefixos="prefixos" :sufixes="sufixes" />   
      </div>
    </div>  
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"

export default {
  name: 'app',
  components: {
    AppItemList: () => import('@/components/AppItemList.vue'),
    AppDomainsList: () => import('@/components/AppDomainsList.vue')
  },
  data() {
    return {
      prefixos: ['Air', 'Jet', 'Flight'],
      sufixes: ['Hub', 'Station', 'Mart']
    }
  }
}
</script>

<style>
#slogan {
  margin-top: 30px;
}
#main {
  background-color: #f1f1f1;
  padding: 30px 0px;
}
</style>
