<template>
    <div>
        <h5>
            {{name}}
            <span class="badge badge-info"> {{ itens.length }} </span>
        </h5>
        <div class="card">
            <div class="card-body">
            <ul class="list-group">
                <li class="list-group-item" v-for="iten in itens" :key="iten">
                <div class="row">
                    <div class="col-md">
                    {{iten}}
                    </div>
                    <div class="col-md text-right">
                    <button 
                        class="btn btn-danger"
                        @click="deleteItem(iten)"
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
                placeholder="digite o item"
                v-model="item"
                @keyup.enter="addItem"
                >
                <div class="input-group-append">
                <button 
                    class="btn btn-info"
                    @click="addItem"
                >
                    <span class="fa fa-plus"></span>
                </button>
                </div>
            </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['name', 'itens'],
    data() {
        return {
            item: ''
        }
    },
    methods: {
        addItem() {
            this.itens.push(this.item);
            this.item = '';
        },
        deleteItem(item) {
            this.itens.splice(this.itens.indexOf(item), 1)
        },
    },
}
</script>