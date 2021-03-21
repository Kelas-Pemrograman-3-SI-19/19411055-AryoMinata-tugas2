<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="form.name"
        label="Nama Lengkap *"
        hint="Nama Lengkap"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Nama Lengkap tidak boleh kosong']"
      />

      <q-input
        filled
        type="number"
        v-model="form.age"
        label="Umur *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Umur tidak boleh kosong'
        ]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
      <div>
        {{ dataset.name }}<br>
        {{ dataset.age }}
      </div>
    </q-form>

  </div>
</template>

<script lang="ts">
export default {
  data () {
    return {
      form: {
        name: null,
        age: null
      },
      dataset: {
        name: null,
        age: null
      },

      accept: false
    }
  },

  methods: {
    onSubmit () {
      this.dataset = this.form
      console.log(this.dataset)
    },

    onReset () {
      this.form.name = null
      this.form.age = null
      this.accept = false
    }
  }
}

</script>
