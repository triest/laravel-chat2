<template>
    <div class="chat-app">
        <Conversation :contacts="SelectedContact" :messages="messages" />

        <Conversation :contacts="Contacts" />
    </div>
</template>

<script>
    import Conversation from './Conversation';
    import ContactsList from './ContactsList';

    export default {
        props: {
            user: {
                type: Object,
                required: true
            }
        },
        data() {
            return {
                SelectedContact: null,
                messages: [],
                conacts: []
            }
        },
        mounted() {
            axios.get('/contacts')
                .then((response) => {
                    console.log(response.data())
                    this.contacts = response.data;
                });
        },
        components: {Conversation, ContactsList}

    }
</script>

<style scoped>

</style>