<template>
    <div class="row">
        <div class="col-8">
            <div class="ard card-default">
                <div class="card-header">Messages</div>

                <div class="card-body">
                    <ul class="list-unstyled" style="height: 300px; overflow-y: scroll">
                        <li class="p-2" v-for="(message, index) in messages" :key="index" >
                            <strong>{{ message.user.name }}</strong>
                                {{ message.message }}
                        </li>
                    </ul>
                </div>
                <input
                    type="text"
                    name="message"
                    placeholder="Enter Your message..."
                    class="form-control">

                <span class="text-muted">User is typing...</span>
            </div>
        </div>


        <div class="col-4">
            <div class="card card-default">
                <div class="card-header">Active Users</div>

                <div class="card-body">
                    <ul>
                        <li class="py-2">Prabin</li>
                    </ul>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                message: []
            }
        },

        created() {
              this.fetchMessages();

        },

        methods:{
            fetchMessages(){
                axios.get('messages').then(response => {
                    this.message = response.data;
                })
            }
        }
    }
</script>
