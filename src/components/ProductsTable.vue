<template>
    <div class="container">  
        <ProductForm @enviar="productos.push($event)"/>
        <hr>
        <h4 class="text-center">Productos</h4>
        <div v-if="productos.length==0" class="alert alert-success">
            No hay productos ingresados
        </div>
        <table v-else class="table table-striped table-hover table-primary">
            <thead>
                <tr>
                    <th scope="col">Id.</th>
                    <th scope="col">Nombre del Producto</th>
                    <th scope="col">Tamaño</th>
                    <th scope="col">Tipo de Ridding</th>
                    <th scope="col">Activo</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, i) of productos" :key="i">
                    <th scope="row">{{i+1}}</th>
                    <td>{{item[i].producto}}</td>
                    <td>{{item[i].tamano}}</td>
                    <td>{{item[i].riddingtype}}</td>
                    <td>{{item[i].activo}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import ProductForm from '../components/ProductForm.vue'
export default {
    
    name:'ProductsTable',
    components: {
        ProductForm,
    },    
    data() {
        return {
            pasa:0,
            productos:[],
        };
    },
}
</script>

<style>

</style>