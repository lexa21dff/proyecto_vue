<template>
    <div>
      <body>
        <Proyecto></Proyecto>
        <Entrega></Entrega> 
       </body>

    </div>
  </template>
  <script>
    import Entrega from '@/components/ListaDeEntregas.vue'
    import Proyecto from '@/components/DetalleProyecto.vue'
   
  
  
    export default {
  
      components: {
        Proyecto, Entrega
      }
  
    }
  </script>