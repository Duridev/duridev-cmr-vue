<script setup>
    import { reactive } from 'vue';
    import RouterLink from '../components/UI/RouterLink.vue'
    import Heading from '@/components/UI/Heading.vue';
    import { FormKit } from '@formkit/vue'

    defineProps({
        titulo: {
            type: String
        }
    })

    const handleSubmit = (data) => {
        console.log('Submit...', data);
    }

    const formData = ({
        telefono: '569'
    })
</script>


<template>
    <div>
        <div class="flex justify-end">
            <RouterLink to="inicio">
                Volver
            </RouterLink>
        </div>
        <Heading>{{ titulo }}</Heading>

        <div class="mx-auto mt-10 bg-white shadow">
            <div class="mx-auto md:w-2/3 py-20 px-6">
                <FormKit
                    type="form"
                    :actions="false"
                    incomplete-message="No se pudo enviar. Completa todos los campos obligatorios"
                    @submit="handleSubmit"
                    :value="formData"
                >
                    <FormKit
                        type="text"
                        label="Nombre"
                        name="nombre"
                        placeholder="Nombre del Cliente"
                        prefix-icon=""
                        validation="required"
                        :validation-messages="{ required: 'El nombre del cliente es obligatorio'}"
                        validation-visibility="blur"
                    />

                    <FormKit
                        type="text"
                        label="Apellido"
                        name="apellido"
                        placeholder="Apellido del Cliente"
                        prefix-icon=""
                        validation="required"
                        :validation-messages="{ required: 'El apellido del cliente es obligatorio'}"
                        validation-visibility="blur"
                    />

                    <FormKit
                        type="email"
                        label="Email"
                        name="email"
                        placeholder="Email del Cliente"
                        prefix-icon=""
                        validation="required|email"
                        :validation-messages="{ required: 'El email del cliente es obligatorio', email: 'Coloca un email válido' }"
                        validation-visibility="blur"
                    />

                    <FormKit
                        type="text"
                        label="Teléfono"
                        name="telefono"
                        placeholder="Teléfono: 56 9 XXXX XXXX"
                        prefix-icon=""
                        validation="required|*matches:/^[0-9]{11}$/"
                        :validation-messages="{ required: 'El teléfono del cliente es obligatorio', matches: 'El formato no es válido'}"
                        validation-visibility="blur"
                    />

                    <FormKit
                        type="text"
                        label="Empresa"
                        name="empresa"
                        placeholder="Empresa a la que pertenece"
                    />

                    <FormKit
                        type="text"
                        label="Cargo"
                        name="cargo"
                        placeholder="Cargo que realiza en la empresa"
                    />

                    <FormKit
                        type="submit"
                        label="Agregar Cliente"
                        incomplete-message="No se pudo enviar. Completa todos los campos obligatorios"
                    />
                    

                </FormKit>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .formkit-wrapper {
        max-width: 100%;
    }

</style>
