<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import DangerButton from "@/Components/DangerButton.vue";
import { Head, Link, useForm } from "@inertiajs/vue3";
import Swal from "sweetalert2";

const props = defineProps({
    departments: { type: Object },
});
const form = useForm({
    id: "",
});

// A function that is called when the delete button is clicked.
const deleteDepartment = () => {
    const alerta = Swal.mixin({
        buttonStyling: true,
    });
    alerta.fire({
        title: 'Are you sure delete '+name+' ?',
        icon: 'question',
        showCancelButton: true,
        confirmButtonText: '<i class="fa-solid fa-check"></i> Yes, delete',
        cancelButtonText: '<i class="fa-solid fa-ban"></i> Cancel',
    }).then((result) => {
        if(result.isConfirmed){
            form.delete(route('departments.destroy',id));
        }
    });
};
</script>

<template>
    <Head title="Departments" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Departments
            </h2>
        </template>

        <div class="py-12">
            <div class="bg-white grid v-screen place-items-center">
                <div
                    class="bg-white overflow-hidden shadow-sm sm:rounded-lg"
                ></div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
