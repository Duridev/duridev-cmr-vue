<script setup>
    import RouterLink from '../components/UI/RouterLink.vue'
    import Heading from '@/components/UI/Heading.vue';
    import { FormKit } from '@formkit/vue'

    defineProps({
        titulo: {
            type: String
        }
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
                >
                    <FormKit
                        type="text"
                        label="Nombre"
                        placeholder="Nombre del Cliente"
                        prefix-icon=""
                        validation="required"
                        :validation-messages="{ required: 'El nombre del cliente es obligatorio'}"
                        validation-visibility="blur"
                    />

                    <FormKit
                        type="text"
                        label="Apellido"
                        placeholder="Apellido del Cliente"
                        prefix-icon=""
                        validation="required"
                        :validation-messages="{ required: 'El apellido del cliente es obligatorio'}"
                        validation-visibility="blur"
                    />

                    <FormKit
                        type="email"
                        label="Email"
                        placeholder="Email del Cliente"
                        prefix-icon=""
                        validation="required|email"
                        :validation-messages="{ required: 'El email del cliente es obligatorio', email: 'Coloca un email válido' }"
                        validation-visibility="blur"
                    />

                    <FormKit
                        type="text"
                        label="Teléfono"
                        placeholder="Teléfono: 56 9 XXXX XXXX"
                        prefix-icon=""
                        validation="required|*matches:/^[0-9]{3}-[0-9]{3}-[0-9]{4}$/"
                        :validation-messages="{ required: 'El teléfono del cliente es obligatorio', matches: 'El formato no es válido'}"
                        validation-visibility="blur"
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
