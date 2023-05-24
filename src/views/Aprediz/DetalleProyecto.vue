<template>
    <div>
        <div class="container">
            <b-card class="m-1 p-3">
                <div class="row">
                    <div class="col-lg-1 col-md-1">
                        <img class="imagen" src="@/assets/2.jpg" alt="">
                    </div>
                    <div class="col-lg-9">
                        <h3>{{ proyecto.nombre }}</h3>
                        <p><span class="fw-lighter">Estado: </span>{{ proyecto.estado }}</p>
                    </div>
                </div>        
                <div class="row">
                    <p class="fw-lighter">Descripcion:</p>
                    <p>{{ proyecto.descripcion }}</p>
                </div>
                
                <div class="row">
                    <p class="fw-lighter">Repositorio en GitHub:</p>
                    <b-link :href="proyecto.codigo_fuente">{{ proyecto.codigo_fuente }}</b-link>
                    <a></a>
                </div>
                <div class="m-1 p-3 position-absolute bottom-0 end-0">
                    <b-button class="m-1  mr-2" @click="editarProyecto(proyecto.id)" variant="warning">
                        <b-icon  icon="pencil"></b-icon> 
                    </b-button>
                    <b-button class="m-1 " @click="eliminarProyecto(entrega)" variant="danger">
                        <b-icon icon="trash"></b-icon>
                    </b-button>
                </div>
            </b-card>
            <div >
                <h3 >Entregas de {{ proyecto.nombre }}</h3>
                <b-card>
                  <b-list-group v-for="entrega in entregas" :key="entrega.id">
                    <b-list-group-item class="d-flex justify-content-between align-items-center">
                        <div class="m-1 p-3">
                            {{ entrega.descripcion_entrega }}
                        </div>
                        <div class="d-flex position-absolute bottom-0 end-0 m-1"  >
                            <div class="ml-auto">
                                <b-button @click="verEntrega(entrega)" variant="primary" class="m-1">
                                    <b-icon icon="eye"></b-icon>
                                </b-button>
                                <b-button @click="editarEntrega(entrega)" variant="warning" class="mr-2">
                                    <b-icon icon="pencil"></b-icon>
                                </b-button>
                                <b-button @click="eliminarEntrega(entrega.id)" variant="danger">
                                    <b-icon icon="trash"></b-icon>
                                </b-button>
                            </div>
                        </div> 
                    </b-list-group-item>
                </b-list-group>
                  <div class="text-end mt-3">
                    <b-button variant="success" @click="crearEntrega()">Crear Entrega</b-button>
                </div>
                </b-card>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default{
    name:'Lista',

    data(){
        return{
            tipo:null,
            proyecto: {
                id:null,
                nombre:null,
                codigo_fuente:null,
                categoria:null,
                descripcion:null,
                estado: null,
            },
            entregas:null
        }
    },
    methods:{
        editarProyecto(id){
            console.log(id)
            this.$router.push('/editar-proyecto/'+id)
        },
        async eliminarEntrega(id){
            console.log(id)
            await axios.delete("http://127.0.0.1:8000/api/entrega/"+id+'/')
            console.log(id)
            await this.getEntregas()
        },
        async getEntregas(){
              await axios.get("http://127.0.0.1:8000/api/entrega/").then(response=>{
              this.entregas= response.data
              console.log(this.entregas)
            })
        },
        crearEntrega(){
            this.$router.push('/crear-entrega/')
        },
        getTipoRevision(url){
              axios.get(url).then(response=>{
                this.tipo=response.data.nombre
                console.log(this.tipo)
            })
        },
        async verProyecto (){
        let id = this.$route.params.id
        await axios.get("http://127.0.0.1:8000/api/proyecto/"+id+"/").then(response=>{
            this.proyecto.id=response.data.id
            this.proyecto.nombre=response.data.nombre_proyecto
            this.proyecto.descripcion=response.data.descripcion
            this.proyecto.estado=response.data.estado
            this.proyecto.codigo_fuente=response.data.codigo_fuente

            });
        }   
    },
    async mounted(){
        await this.verProyecto()
        await this.getEntregas()
    }
}
</script>
<style>
.imagen{
    width: 100%;
}

</style>