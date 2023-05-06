<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-12">
        <h1>Regitro de Miembros de la Familia Tornero</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12">
        <formulario-persona v-on:add-persona="agregarPersona" />
        <tabla-personas v-bind:personas="personas" v-on:delete-persona="eliminarPersona"  v-on:actualizar-persona="actualizarPersona"
/>        
      </div>
    </div>
  </div>

  <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App - Rubenz"/>
</template>
<script>
import TablaPersonas from '@/components/TablaPersonas.vue'
import FormularioPersona from '@/components/FormularioPersona.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    TablaPersonas,
    FormularioPersona,
    HelloWorld
  },
  data() {
    return {
      personas: [
        {
          id: 1,
          nombre: 'Ruben',
          apellido: 'Tornero',
          email: 'rtornero@gmail.com',
        },
        {
          id: 2,
          nombre: 'Adrien',
          apellido: 'Tornero',
          email: 'atornero@gmail.com',
        },
        {
          id: 3,
          nombre: 'Francy',
          apellido: 'Morales',
          email: 'fmorales@gmail.com',
        },
        {
          id: 4,
          nombre: 'Alessia',
          apellido: 'Tornero',
          email: 'altornero@gmail.com',
        },
      ],
    }
  },
  methods: {
  agregarPersona(persona) {
    console.log('evento recibido');
    //console.log(persona);
    let id = 0;
    
    if (this.personas.length > 0) {
      id = this.personas[this.personas.length - 1].id + 1;
    }
    
    this.personas= [...this.personas, { ...persona, id}];
  },
  eliminarPersona(id) {
    this.personas = this.personas.filter(
      persona => persona.id !== id
    );
  },
  actualizarPersona(id, personaActualizada) {
      this.personas = this.personas.map(persona =>
      persona.id === id ? personaActualizada : persona
    )
  }
}
}
</script>

<style>
  button {
    background: #009435;
    border: 1px solid #009435;
  }

  #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>



