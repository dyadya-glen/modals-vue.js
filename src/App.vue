<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <section>
        <div class="container">

          <!-- first modal -->
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show first modal</button>
          <modals title="First modal"
          v-show="modalFirst"
          @close="modalFirst = false">
            <!-- body -->
            <div slot="body">
              <p>Text Text Text Text Text Text Text</p>
              <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Well Done!</button>
            </div>
          </modals>

          <!-- Second modal -->
          <button class="btn btnPrimary" @click="modalSecond.show = !modalSecond.show">Show modal with form</button>
          <modals title="Modal with form"
          v-show="modalSecond.show"
          @close="modalSecond.show = false">
            <!-- body -->
            <div slot="body">
              <form @submit.prevent="submitSecondForm">
                <label>Name</label>
                <input type="text" v-model="modalSecond.name" required>
                <label>Email</label>
                <input type="email" v-model="modalSecond.email" required>
                <button class="btn btnPrimary">Submit</button>
              </form>
            </div>
          </modals>

          <!-- modal with validate -->
          <button class="btn btnPrimary" @click="modalValidate = !modalValidate">Show modal with form + Validate</button>
          <modalValidate v-show="modalValidate" @close="modalValidate = false"/>

          <!-- modal with validate password -->
          <button class="btn btnPrimary" @click="modalValidatePass = !modalValidatePass">Show modal with form + Validate +Password</button>
          <modalValidatePass v-show="modalValidatePass" @close="modalValidatePass = false"/>
        </div>
      </section>


    </div>
  </div>
</template>

<script>
import modals from '@/components/UI/Modal.vue'
import modalValidate from '@/components/ModalValidate.vue'
import modalValidatePass from '@/components/ModalValidatePass.vue'
export default {
  components: { modals, modalValidate, modalValidatePass },
  data () {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: '',
        email: ''
      },
      modalValidate: false,
      modalValidatePass: false
    }
  },
  methods: {
    submitSecondForm () {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email
      })
      this.modalSecond.name = ''
      this.modalSecond.email = ''
      this.modalSecond.show = false
    }
  }
}
</script>

<style>
 .btn {
   margin: 10px 5px;
 }
</style>
