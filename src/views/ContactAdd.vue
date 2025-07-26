<template>
    <div v-if="contact" class="page">
        <h4>Them Lien He</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="contactAdd"
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
    import ContactForm from '@/components/ContactForm.vue';
    import contactService from '@/services/contact.service';

    export default {
        components: {
            ContactForm,
        },

        data(){
            return {
                contact: {},
                message: "",
            };
        },

        methods: {
            async contactAdd(data) {
                try{
                    await contactService.create(data);
                    this.$router.push({ name: "contactbook"});
                } catch(error){
                    console.log(error);
                }
            },
        },

        created(){

        },
    };
</script>