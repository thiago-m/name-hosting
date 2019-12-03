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
            <h5>
              Prefixos
              <span class="badge badge-info"> {{ prefixos.length }} </span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="prefix in prefixos" :key="prefix">
                    {{prefix}}
                  </li>
                </ul>
                <br>
                <input type="text" class="form-control" placeholder="Digite o prefixo">
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              Sufixos
              <span class="badge badge-info"> {{ sufixes.length }} </span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="sufix in sufixes" :key="sufix">
                    {{sufix}}
                  </li>
                </ul>
                <br>
                <input type="text" class="form-control" placeholder="Digite o sufixos">
              </div>
            </div>
          </div>
        </div>
        <br>
        <h5>
          Domínios
          <span class="badge badge-info"> {{ domains.length }} </span>
        </h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li class="list-group-item" v-for="domain in domains" :key="domain">
                {{ domain }}
              </li>
            </ul>
          </div>
        </div> 
      </div>
    </div>  
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"

export default {
  name: 'app',
  data() {
    return {
      prefixos: ['Air', 'Jet', 'Flight'],
      sufixes: ['Hub', 'Station', 'Mart'],
      domains: ['AirHub', 'AirStation', 'AirMart']
    }
  }
}
</script>

<style>
#slogan {
  margin: 30px 0px;
}
#main {
  background-color: #f1f1f1;
  padding: 30px 0px;
}
</style>
