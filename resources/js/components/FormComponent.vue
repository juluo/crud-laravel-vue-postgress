 <template>
    <div class="col-md-8">
            <div class="card">
                <div class="card-header">En que estas pensando ahora?</div>
                <div class="card-body">

                    <!-- <div class="alert alert-success" role="alert">
                    </div> -->

                    <form action="" v-on:submit.prevent="newThrought()">
                        <div class="form-group">
                            <label for="">Ahora estoy pensando en</label>
                            <input type="text" class="form-control" name="throught" v-model="description">
                        </div>

                        <button class="btn btn-primary">Enviar Pensamiento</button>
                    </form>
                </div>
            </div>
        </div>    
</template>


<script>
    export default {
        data(){
            return{
                description:''
            }
        },
        mounted() {
            console.log('Component mounted.')
        },
        methods: {
            newThrought(){

                const params = {
                    description: this.description
                };

                axios.post('/throughts', params)
                     .them((response) => console.log(response));

                let throught = {
                    id: 2,
                    description: this.description,
                    create_at: '11/22/2013'
                };
                this.$emit('new',throught);
                this.description = '';
            }
        }
    }
</script>
