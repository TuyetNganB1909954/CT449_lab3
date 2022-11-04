<template>
    <div v-if="contact" class="page">
        <h4>Thêm Liên hệ mới</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="createContact"
        />
        <p>{{ message }}</p>
    </div>
</template>
<script>
    import ContactForm from "@/components/ContactForm.vue";
    import ContactService from "@/services/contact.service";
    import axios from 'axios'
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
           
            async createContact() {
                try {
                    await ContactService.create(this.contact)
                    this.message = "Liên hệ được cập nhật thành công.";
                } catch (error) {
                    console.log(error);
                }
            },
           
        },
       
    };
</script>