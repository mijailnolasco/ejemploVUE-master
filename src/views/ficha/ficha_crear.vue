<template>
    <div class="row">
        <div class="col-md-12">
            <div class="card">
                <div class="card-body">
                    <h1>FICHA DE INSCRIPCION DEL PARTICIPANTE</h1>
                    <h2>II CONCURSO</h2>
                    <div class="mb-3">
                        <label class="form-label">datos del alumno participante</label>
                        <input v-model="ficha_datos_del_alumno_participante" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                                <label class="form-label">nombres</label>
                                <input v-model="ficha.nombres" type="text" class="form-control">
                            </div>
                    <div class="row">
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">apellidos</label>
                                <input v-model="ficha.apellidos" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label"> dni</label>
                                <input v-model="ficha.dni" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">ficha_de_nacimiento</label>
                                <input v-model="ficha.ficha_de_nacimiento" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">sexo</label>
                                <input v-model="ficha.sexo" type="text" class="form-control">
                            </div>
                        </div>
                    </div>
                    
                    <div class="mb-3">
                        <label class="form-label">edad</label>
                        <input v-model="ficha.edad" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">telefono celular</label>
                        <input v-model="ficha.telefono_celular" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">telefono fijo</label>
                        <input v-model="ficha.telefono_fijo" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">email</label>
                        <input v-model="ficha.email" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">estudio_canto</label>
                        <input v-model="ficha.estudio_canto" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">cuanto_tiempo</label>
                        <input v-model="ficha.cuanto_tiempo" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">que_fondo_musical_usara</label>
                        <input v-model="ficha.que_fondo_musical_usara" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">marque_con_una_x</label>
                        <input v-model="ficha.marque_con_una_x" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">usara_pista_musical</label>
                        <input v-model="ficha.usara_pista_musical" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">llevara_acompañamiento_musical</label>
                        <input v-model="ficha.llevara_acompañamiento_musical" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">datos_del_centro_educativo</label>
                        <input v-model="ficha.datos_del_centro_educativo" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">nombres</label>
                        <input v-model="ficha.nombres" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">direccion</label>
                        <input v-model="ficha.direccion" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">datos_del_docente_representante_del_centro_educativo</label>
                        <input v-model="ficha.datos_del_docente_representante_del_centro_educativo" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">nombres</label>
                        <input v-model="ficha.nombres" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">apellidos</label>
                        <input v-model="ficha.apellidos" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">telefono celular</label>
                        <input v-model="ficha.telefono_celular" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">telefono_fijo</label>
                        <input v-model="ficha.telefono_fijo" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">email</label>
                        <input v-model="ficha.email" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">anexar_fotocopia_dni_fotos</label>
                        <input v-model="ficha.anexar_fotocopia_dni_fotos" type="text" class="form-control">
                    </div>
                 
                </div>
            </div>
        </div>
        <div class="col-md-12">
            <button @click="guardar()" type="button" class="btn btn-primary">Guardar</button>
            <RouterLink class="btn btn-light" to="/ficha_listar">Cancelar</RouterLink>
        </div>
    </div>
</template>
<script>

import { collection, getDocs, query, where,addDoc } from "firebase/firestore";
import { auth, db } from "../../firebaseConfig";
import { defineComponent } from 'vue';
export default defineComponent({
    // name: 'scanner',
    data() {
        return {
            loadingDoc: false,
            ficha: {
                nombres: '',
                apellidos: '',
                dni: '',
                ficha_de_nacimiento: '',
                sexo: '',
                edad: '',
                telefono_celular: '',
                telefono_fijo:'',
                email: '',
                estudio_canto: '',
                cuanto_tiempo: '',
                que_fondo_musical_usara: '',
                marque_con_una_x: '',
                usara_pista_musical: '',
                llevara_acompañamiento_musical: '',
                datos_del_centro_educativo: '',
                nombres: '',
                apellidos: '',
                telefono_celular: '',
                telefono_fijo: '',
                email: '',
                anexar_fotocopia_dni_fotos: '',
            },
        }
    },
    methods: {
        async guardar() {
            try {
                const q = query(collection(db, 'ficha'));
                const docRef = await addDoc(q, this.ficha);
                this.$router.push({ name: 'ficha_listar' })
            } catch (error) {
                console.log(error);
            } 
        },
    },
    created() {
    }
})
</script>