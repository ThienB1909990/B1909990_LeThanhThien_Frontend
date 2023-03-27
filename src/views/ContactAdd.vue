<template>
    <div class="page">
        <h4>Tạo liên hệ mới</h4>
        <ContactForm :contact="contact" @submit:contact="AddContact" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: {},
            message: "",
        };
    },
    methods: {
        async AddContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Tạo thành công!!!";
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>