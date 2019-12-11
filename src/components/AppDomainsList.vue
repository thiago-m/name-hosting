<template>
    <div>
        <h5>
            Domínios
            <span class="badge badge-info"> {{ domains.length }} </span>
        </h5>
        <div class="card">
            <div class="card-body">
            <ul class="list-group">
                <li class="list-group-item" v-for="domain in domains" :key="domain.name">
                <div class="row">
                    <div class="col-md">
                    {{ domain.name }}
                    </div>
                    <div class="col-md text-right">
                    <a class="btn btn-info" :href="domain.checkout" target="_blank">
                        <span class="fa fa-shopping-cart"></span>
                    </a>
                    </div>
                </div>
                </li>
            </ul>
            </div>
        </div> 
    </div>
</template>

<script>
export default {
  props: ['prefixos', 'sufixes'],
  computed: {
    domains() {
      let domain = []
      for (const prefix of this.prefixos) {
        for (const sufix of this.sufixes) {
          const name = prefix + sufix
          const url = name.toLowerCase();
          const checkout = `https://checkout.hostgator.com.br/?a=add&sld=${url}&tld=.com`
          domain.push({name, checkout});
        }
      }
      return domain;
    }
  }
}
</script>