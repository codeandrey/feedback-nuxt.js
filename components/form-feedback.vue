<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset">
      <b-form-group
        id="input-group-1"
        label="Telephone:"
        label-for="tel-1" >
        <b-form-input
          id="tel-1"
          v-model="form.tel"
          type="tel"
          v-mask="'+7(999) 999-9999'"
          required
          placeholder="Enter telephone"
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.name"
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>
     <b-form-checkbox
          id="checkbox-1"
          v-model="form.checkbox"
          name="checkbox-1"
          value="accepted"
          unchecked-value="not_accepted"
        >Согласен на обработку персональных данных
      </b-form-checkbox>
      <b-button type="submit" :disabled="!isValidForm" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import MaskedInput from 'vue-masked-input'

  export default {
    data() {
      return {
        form: {
          tel: '',
          name: '',
          checkbox: 'accepted'
        }
      }
    },
     computed: {
      isValidForm : function(){
        let valid = (this.form.checkbox=='accepted') ? true : false
        return valid
      }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
      },
      onReset(evt) {
        evt.preventDefault()
        // Reset our form values
        this.form.tel = ''
        this.form.name = ''
        this.form.checkbox = 'accepted'
      }
    }
  }
</script>
