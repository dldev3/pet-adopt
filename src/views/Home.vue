<template>
  <div class="home-view-container mb-5">
    <h1>Adopt a new best friend</h1>
    <h3>Animals' Count {{animalsCount}}</h3>
    {{ getAllCats.length }}
    <button @click="togglePetForm()" class="btn btn-primary mb-3"><span v-if="!showPetForm">Add New Pet</span><span v-else>Hide Form</span></button>

    <b-form @submit.prevent="handleSubmit" v-if="showPetForm">

      <b-form-group label="Pet's Name:">
        <b-form-input
          v-model="formData.name"
          placeholder="Enter Pet's Name"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Pet's Age:">
        <b-form-input
          type="number"
          v-model="formData.age"
          placeholder="Enter Pet's Age"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Pet's Breed:">
        <b-form-input
          type="text"
          v-model="formData.breed"
          placeholder="Enter Pet's Breed"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Pet's Location:">
        <b-form-input
          type="text"
          v-model="formData.location"
          placeholder="Enter Pet's Location"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Pet's Color:">
        <b-form-input
          type="text"
          v-model="formData.color"
          placeholder="Enter Pet's Color"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Pet's Weight:">
        <b-form-input
          type="number"
          v-model="formData.weight"
          placeholder="Enter Pet's Weight"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Some Informations:">
        <b-form-input
          type="text"
          v-model="formData.notes"
          placeholder="Enter Notes here"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Gender:">
        <b-form-select
          v-model="formData.gender"
          :options="['male', 'female']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group label="Species:">
        <b-form-select
          v-model="formData.species"
          :options="['cats', 'dogs']"
          required
        ></b-form-select>
      </b-form-group>

      <b-button type="submit" variant="primary" class="mr-2">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>

  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex';

export default {
  data: function(){
    return {
      formData: {
          name: '',
          age: 0,
          color: '',
          weight: 0,
          species: null,
          breed: '',
          gender: null,
          location: '',
          notes: ''
        },
      showPetForm: false
    }
  },
  computed: {
    ...mapGetters([
      'animalsCount',
      'getAllCats'
    ])
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm(){
      this.showPetForm = !this.showPetForm
    },
    handleSubmit(){
      const { species, name, age, breed, gender,location, notes,color, weight } = this.formData;
      const payload = {
          species,
          pet: {
            name,
            age,
            color,
            weight,
            gender,
            breed,
            location,
            notes
          }
      };
      this.addPet(payload);

      // reset the form after Submit
      this.formData= {
        name: '',
        age: 0,
        color: '',
        weight: 0,
        species: null,
        breed: '',
        gender: null,
        location: '',
        notes: ''
      }
    }
  }
}
</script>
