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
                    id="phone"
                    v-model="item.phone"
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
                phone:""
            }
        }
    },
     methods: {
         save() {
             try{
                 axios.post('/api/tel', this.item)
                 .then(res=> {

                 })   
             } catch (e) {
                 console.log(e)
             }
         }
     }
}
</script>

<style>

</style>