<template>
    <div class="row">
        <div class="col-md-12">
            <RouterLink class="btn btn-primary" to="/ficha_crear">Agregar Ficha</RouterLink>
        </div>
        <div class="col-md-12">
            <div class="card">
                <div class="card-body">
                    <table class="table">
                        <thead>
                            <tr>
                                <th scope="col">nombres</th>
                                <th scope="col">apellidos</th>
                                <th scope="col">DNI</th>
                                <th scope="col">ficha_de_nacimiento</th>
                                <th scope="col">sexo</th>
                                <th scope="col">edad</th>
                                <th scope="col">telefono_celular</th>
                                <th scope="col">telefono_fijo</th>
                                <th scope="col">e_mail</th>
                                <th scope="col">estudio_canto</th>
                                <th scope="col">cuanto_tiempo</th>
                                <th scope="col">que_fondo_musical_usara</th>
                                <th scope="col">llevara_acompañamiento_musical</th>
                                <th scope="col">datos_del_centro_educativo</th>
                                <th scope="col">nombres</th>
                                <th scope="col">apellidos</th>
                                <th scope="col">telefono_celular</th>
                                <th scope="col">telefono_fijo</th>
                                <th scope="col">e_mail</th>
                                <th scope="col">anexar_fotocopia_dni_fotos</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="data in ficha">
                                <td>{{ data.nombres }}</td>
                                <td>{{ data.apellidos }}</td>
                                <td>{{ data.dni }}</td>
                                <td>{{ data.ficha_de_nacimiento }}</td>
                                <td>{{ data.sexo }}</td>
                                <td>{{ data.edad }}</td>
                                <td>{{ data.telefono_celular }}</td>
                                <td>{{ data.telefono_fijo }}</td>
                                <td>{{ data.e_mail }}</td>
                                <td>{{ data.estudio_canto }}</td>
                                <td>{{ data.cuanto_tiempo }}</td>
                                <td>{{ data.que_fondo_musical_usara }}</td>
                                <td>{{ data.marque_con_una_x }}</td>
                                <td>{{ data.que_pista_musical_usara }}</td>
                                <td>{{ data.llevara_acompañamiento_musical }}</td>
                                <td>{{ data.datos_del_centro_educativo }}</td>
                                <td>{{ data.nombres }}</td>
                                <td>{{ data.apellidos }}</td>
                                <td>{{ data.telefono_celular }}</td>
                                <td>{{ data.telefono_fijo }}</td>
                                <td>{{ data.e_mail }}</td>
                                <td>{{ data.anexar_fotocopia_dni_fotos }}</td>
                                <td>
                                    <RouterLink class="btn btn-success" :to="'/ficha_editar/' + data.id">Editar</RouterLink>
                                    <button class="btn btn-danger" @click="eliminar(data.id)">Eliminar
                                    </button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import { collection, getDocs, query, where,deleteDoc,doc } from "firebase/firestore";
import { auth, db } from "../../firebaseConfig";

import { defineComponent } from 'vue';
export default defineComponent({
    data() {
        return {
            loadingDoc: false,
            ficha: []
        }
    },

    methods: {
        async getUrls() {
            try {
                this.ficha= []
                const q = query(
                    collection(db, "ficha")
                );
                const querySnapshot = await getDocs(q);
                querySnapshot.forEach((doc) => {
                    // console.log(doc.id);
                    this.ficha.push({
                        nombre: doc.data().nombre,
                        dni: doc.data().dni,
                        profesion: doc.data().profesion,
                        id: doc.id,
                        // ...doc.data()
                    });
                });
                // console.log(this.curso);
            } catch (error) {
                console.log(error);
            }
        },
        async eliminar(id) {
            try {
                const q = doc(db, "ficha", id);
                const docRef = await deleteDoc(q);
                this.getUrls()
            } catch (error) {
                console.log(error);
            }
        },
    },
    mounted() {
        this.getUrls()
    }
})
</script>