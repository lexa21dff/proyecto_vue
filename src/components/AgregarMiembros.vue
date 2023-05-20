<template>
    <div>
      <h2 class="p-3 text-center">Lista Inscritos</h2>
      <div class="container">
        <form class="form-inline" @submit.prevent="agregarMiembro">
          <table class="table table-hover">
            <thead>
              <tr>
                <th>Inscritos</th>
                <th>Accion</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(inscrito, index) in inscritos" :key="index">
                <td>{{ inscrito.perfil }}</td>
                <button @click="agregar(inscrito.id)" class="btn btn-outline-success" >Agregar</button>
              </tr>
            </tbody>
          </table>
        </form>
      </div>
      <!-- <button type="submit" class="btn btn-outline-success">Agregar miembro</button> -->
      <button class="btn btn-outline-danger" @click="cancelar">Cancelar</button>
    </div>
  </template>
    
  <script>
  import axios from 'axios';
    
    export default{
      name: 'crear',
      data(){
        return{
          errors:[],
          inscritos:[],
          // grupos:[],
          // perfiles:[],
          // fichas:[]
        }
      },
      created(){
        this.obtenerInscritos();
        // this.obtenerPerfiles();
        // this.obtenerFichas();
      },
      
      methods:{
        
        async obtenerInscritos(){
          const respuesta = await axios.get('http://127.0.0.1:8000/api/inscrito/');
          this.inscritos = respuesta.data;
          
        // },
        // async obtenerPerfiles(){
        //   const respuesta = await axios.get('http://127.0.0.1:8000/api/perfil/');
        //   this.perfiles = respuesta.data;
          
        // },
        // async obtenerFichas(){
        //   const respuesta = await axios.get('http://127.0.0.1:8000/api/ficha/');
        //   this.fichas = respuesta.data;
          
        // },
        // async agregarMiembro(id){
        //   await axios.post('http://127.0.0.1:8000/api/inscrito/', this.inscrito);
        //   this.$router.push('/grupo/'+id)
        },
        cancelar() {
          this.$router.push('/CrearGrupo');
        }
        
      }
  
    } 
  </script>
  
  
    
    