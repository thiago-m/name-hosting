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
                    <div class="row">
                      <div class="col-md">
                        {{prefix}}
                      </div>
                      <div class="col-md text-right">
                        <button 
                          class="btn btn-danger"
                          @click="deletePrefix(prefix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br>
                <div class="input-group">
                  <input 
                    type="text" 
                    class="form-control" 
                    placeholder="Digite o prefixo"
                    v-model="prefix"
                    @keyup.enter="addPrefix"
                  >
                  <div class="input-group-append">
                    <button 
                      class="btn btn-info"
                      @click="addPrefix"
                    >
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
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
                    <div class="row">
                      <div class="col-md">
                        {{sufix}}
                      </div>
                      <div class="col-md text-right">
                        <button 
                          class="btn btn-danger"
                          @click="deleteSufix(sufix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br>
                <div class="input-group">
                <input 
                  type="text" 
                  class="form-control" 
                  placeholder="Digite o sufixos"
                  v-model="sufix"
                  @keyup.enter="addSufix"
                >
                  <div class="input-group-append">
                    <button 
                      class="btn btn-info"
                      @click="addSufix"
                    >
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
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
      prefixos: [],
      sufixes: [],
      domains: [],
      prefix: '',
      sufix: ''
    }
  },
  methods: {
    addPrefix() {
      this.prefixos.push(this.prefix);
      this.prefix = '';
      this.generate()
    },
    addSufix() {
      this.sufixes.push(this.sufix);
      this.sufix = '';
      this.generate()
    },
    deletePrefix(prefix) {
      this.prefixos.splice(this.prefixos.indexOf(prefix), 1)
      this.generate()
    },
    deleteSufix(sufix) {
      this.sufixes.splice(this.sufixes.indexOf(sufix), 1)
      this.generate()
    },
    generate() {
      this.domains = [];
      for (const prefix of this.prefixos) {
        for (const sufix of this.sufixes) {
          this.domains.push(prefix + sufix);
        }
      }
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
