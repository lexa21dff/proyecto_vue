<template>
  <div>
    <body>
      <Carrusel> </Carrusel>  
      <ul>
        <Informacion> </Informacion>
      </ul>
      <ul>
        <Ideas> </Ideas>
      </ul>
      <b-img src="https://res-console.cloudinary.com/dt5mbmxva/thumbnails/transform/v1/image/upload/Y19zY2FsZSxoXzMxNSx3XzEyOTg=/v1682784977/dGFtYW5vcy1kZS1sYXMtaW1hZ2VuZXMtZGUtbGFzLXJlZGVzLXNvY2lhbGVzX3RlNjZmbA==/template_primary" fluid-grow alt="Fluid-grow image"></b-img>
    </body>
    <Footer>
    </Footer>
  </div>
</template>
<script>
  
  import Footer from '../components/Footer.vue'
  import Carrusel from '../components/Carrusel.vue'
  import Informacion from '../components/Informacion.vue'
  import Ideas from '../components/Ideas.vue'


  export default {

    components: {
       Footer, Carrusel, Informacion, Ideas
    }

  }
</script>

<style>





</style>

