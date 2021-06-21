<template>
    <div>
        <!-- <h2>{{ myName }}</h2> -->
        <div class="mb-2">
            <div class="mb-2">
                <label for="name" class="form-label">Name</label>
                <input
                    type="text"
                    placeholder="Enter Name"
                    class="form-control"
                    id="name"
                    v-model="item.name"
                >
            </div>
            <div class="mb-2">
                <label for="phone" class="form-label">Telephone Number</label>
                <input
                    type="text"
                    placeholder="Enter Phone Number"
                    class="form-control"
                    id="tel"
                    v-model="item.tel"
                >
            </div>
            <div class="d-grid">
                <button 
                    class="btn btn-success btn-block"
                    @click="save"  
                >
                    Save
                </button>
            </div>
            <div class="col-md-12 mt-3" v-if="lists.length > 0">
                <h2 class="text-center">Telephone Numbers</h2>
                <ul class="list-group">
                    <li 
                        class="list-group-item"
                        v-for="item in lists"
                        :key="item.id"
                        >
                        {{ item.name }} - {{item.tel}}
                        <span class="float-right">
                            <button 
                                class="btn btn-warning btn-sm mr-2">
                                View
                            </button>
                            <button 
                                class="btn btn-danger btn-sm mr-2"
                                @click="deleteTel(item.id)"
                                >
                                Delete
                            </button>
                        </span>

                    </li>
                </ul>
            </div>
        </div>
    </div>
    
</template>

<script>
export default {
    name : 'Directory',
    data() {
        return {
            // myName: "Perosonal Contact"
            lists: [],
            item: {
                name:"",
                tel:""
            }
        }
    },
    mounted() {
        this.fetchAll();
    },
     methods: { 
         fetchAll(){
             axios.get('/api/tel')
                 .then(res => this.lists = res.data)
         },
         save() {
             try{
                 axios.post('/api/tel', this.item)
                 .then(res=> {

                 })   
             } catch (e) {
                 console.log(e)
             }
         },
         deleteTel(id){
             try{
                 axios.delete(`/api/tel/${id}`)
                 .then(res => this.fetchAll())   
             } catch (e) {
                 //console.log(e)
             }
         }
         }
     }
</script>

<style>

</style>