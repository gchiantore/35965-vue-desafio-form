<template>
    <div class="container">
        <div v-if="errores.length!=0" class="alert alert-danger">
            {{showErrors}}
        </div>
        <div class="row">
            <div class="col-md-3"></div>
            <div class="col-md-6">
                <form class="row g-3 needs-validation" id="productform" action="" @submit.prevent="formValidate">
                    <div class="col-md-12">
                        <label for="producto" class="form-label">Nombre del Producto</label>
                        <input v-model="objproducto.producto" type="text" class="form-control" id="producto" value="">
                    </div>
                    <div class="col-md-12">
                        <label for="tamaño" class="form-label">Tamaño</label>
                        <select v-model="objproducto.tamano" class="form-select" id="tamaño">
                            <option selected disabled value=""></option>
                            <option value="9">9 metros</option>
                            <option value="12">12 metros</option>
                            <option value="14">14 metros</option>
                        </select>
                    </div>
                    <h5>Estilo de Ridding</h5>
                    <div class="col-4">
                        <div class="form-check">
                            <input v-model="objproducto.riddingtype" class="form-check-input" type="checkbox" value="Wave" id="wave">
                            <label class="form-check-label" for="wave">
                                Wave
                            </label>
                        </div>
                    </div>
                    <div class="col-4">
                        <div class="form-check">
                            <input v-model="objproducto.riddingtype" class="form-check-input" type="checkbox" value="Freestyle" id="freerstyle">
                            <label class="form-check-label" for="freestyle">
                                Freestyle
                            </label>
                        </div>
                    </div>
                    <div class="col-4">
                        <div class="form-check">
                            <input v-model="objproducto.riddingtype" class="form-check-input" type="checkbox" value="Big Air" id="bigair">
                            <label class="form-check-label" for="bigair">
                                Big Air
                            </label>
                        </div>
                    </div>
                    <h5>Activo</h5>
                    <div class="row">
                        <div class="form-check col-md-4">
                            <input v-model="objproducto.activo" class="form-check-input" type="radio" name="flexRadioDefault" id="afirmativo" value="SI" checked>
                            <label class="form-check-label" for="avirmativo">
                                SI
                            </label>
                        </div>
                            <div class="form-check col-md-4">
                            <input v-model="objproducto.activo" class="form-check-input" type="radio" name="flexRadioDefault" id="negativo" value="NO">
                            <label class="form-check-label" for="negativo">
                                NO
                            </label>
                        </div>
                    </div>
                    <div class="col-12">
                        <button class="btn btn-primary" type="submit">Agregar Producto</button>
                    </div>
                </form>
            </div>
                <div class="col-md-3"></div>
        </div>
    </div>
</template>

<script>
export default {
    name:'ProductForm',
    data() {
        return {
            objproducto:{
                producto:'',
                tamano:'',
                riddingtype:[],
                activo:'SI',
            },
            errores:[]
        }
    },    
    methods: {
        formValidate() {
            console.log(this.objproducto.riddingtype.length)
        if(this.objproducto.producto && this.objproducto.riddingtype.length!=0 && this.objproducto.tamano){
            alert("Enviando formulario!");
            setTimeout(() => {
                console.log("Entro Aqui!")
                this.$emit("enviar",this.objproducto);
                document.getElementById("productform").reset();
                Object.assign(this.$data, this.$options.data());
            }, 3000);
            return true;
        }
        if(!this.objproducto.producto){
            this.errores.push("El nombre del producto es necesario ");
        }
        if(!this.objproducto.tamano){
            this.errores.push("Debes seleccionar un Tamaño");
        }
        if(this.objproducto.riddingtype.length == 0){
            this.errores.push("Debes elegir un tipo de Ridding")
        } 
        setTimeout(() => {
            this.errores=[];
        }, 3000);

        console.log("pasa de largo   "+this.objproducto.producto + this.objproducto.riddingtype)    
        }
        
    },
    computed: {
        showErrors() {
            let formErrores=this.errores.join(" ");
            return formErrores;
        }
    },
}
</script>

<style>

</style>