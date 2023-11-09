<template>
    <div>
        <button 
        type="button" 
        class="btn btn-primary" 
        data-bs-toggle="modal" 
        data-bs-target="#exampleModal" 
        data-bs-whatever="@mdo">Add List
        </button>

        <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
          <div class="modal-dialog">
            <div class="modal-content">
              <div class="modal-header">
                <h1 class="modal-title fs-5" id="exampleModalLabel">New List</h1>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
              </div>
              <div class="modal-body">
                <form>
                  <div class="mb-3">
                    <label for="recipient-name" class="col-form-label">List name:</label>
                    <Input
                    class="new-movie-label" 
                    placeholder="List name" 
                    v-model="name"
                    @input="name = $event.target.value"/>
                  </div>
                  <div class="mb-3">
                    <label for="recipient-name" class="col-form-label">Longitude:</label>
                    <Input
                    class="new-movie-label"
                    placeholder="Longitude"
                    type="number"
                    v-model="viewers"
                    @input="viewers = $event.target.value"/>
                  </div>
                  <!-- <div class="mb-3">
                    <label for="recipient-name" class="col-form-label">Latitude:</label>
                    <Input
                    class="new-movie-label"
                    placeholder="Nechi marotaba ko'rilgan?"
                    type="number"
                    v-model="viewers"
                    @input="viewers = $event.target.value"/>
                  </div> -->
                </form>
              </div>
              <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                <PrimaryButton 
                class="btn-outline-dark" 
                type="submit" 
                @click="addMovie">Save</PrimaryButton>
              </div>
            </div>
          </div>
         </div>
    </div>
</template>

<script>
import Input from "@/ui-components/Input.vue";

export default {
    components: {Input},
    data(){
        return{
            name: '',
            viewers: '',
        }
    },
    methods: {
        addMovie() {
            if(!this.name || !this.viewers) return
            const newMovie = {
                name: this.name,
                viewers: this.viewers,
                favourite: false,
                like: false,
            }
            this.$emit('createMovie', newMovie) //ona divga ma'lumot jo'natish
            this.name = ''
            this.viewers = ''
        },
    },
}
</script>

<style>
</style>