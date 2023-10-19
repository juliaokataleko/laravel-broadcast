<template>
    <div>
        <div>
            Message: 

            <div v-for="message in messages" :key="message">
                <div>{{ message }}</div>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        data() {
            return {
                messages: []
            }
        },
        created() {
            console.log('Component created.')

            Echo.channel('notification').listen('MessageNotification', (e) => {
                console.log("Mensagem recebida...");

                console.log(e);
                this.messages.push(e.message)
                
            })
        },
        mounted() {

            // Echo.channel('notification').listen(
            //     'MessageNotification',
            //     (e) => {
            //         console.log("Mensagem recebida...");
            //     }
            // )
        }
    }
</script>
