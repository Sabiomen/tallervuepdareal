<template>
  <div>
                <h1>{{ listaNombre }}</h1>
                <h3>{{ modificarNombreLista }}</h3>
                <input type="text" v-model="nuevoNombreLista" @keyup.enter="renombrarLista">
                <br><br>
                <ul>
                    <li v-for="(tarea, index) in listaTareas" :key="index">
                        {{ tarea }}
                        <button style="background-color: salmon;" @click="eliminarTarea(index)">Eliminar</button>
                        <input type="text" v-model="tareaModificada[index]" @keyup.enter="modificarTarea(index)">
                    </li>
                    <h4>{{ headsupModificar }}</h4>
                    <br><br>
                </ul>
                <h2>{{ nuevaTareaNombre }}</h2>
                <input type="text" v-model="nuevaTarea" @keyup.enter="agregarTarea">
            </div>
</template>

<script>
export default {
            data() {
                return {
                    listaNombre: 'Lista de Quehaceres',
                    modificarNombreLista: 'Modificar nombre de Lista',
                    nuevaTareaNombre: 'Crear tarea nueva',
                    nuevaTarea: '',
                    listaTareas: [],
                    nuevoNombreLista: '',
                    tareaModificada: [],
                    headsupModificar: 'Para editar el nombre de una tarea, escriba un nombre nuevo y presione "Enter".'
                }
            },
            methods: {
                renombrarLista() {
                    this.listaNombre = this.nuevoNombreLista;
                    this.nuevoNombreLista = '';
                },
                agregarTarea() {
                    if (this.nuevaTarea.trim() !== '') {
                        this.listaTareas.push(this.nuevaTarea);
                        this.nuevaTarea = '';
                    }
                },
                eliminarTarea(index) {
                    this.listaTareas.splice(index, 1);
                },
                modificarTarea(index) {
                    if (this.tareaModificada[index].trim() !== '') {
                        this.listaTareas[index] = this.tareaModificada[index];
                        this.tareaModificada[index] = '';
                    }
                }
            }
          };
</script>


<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
