<template>
  <b-container>
    <div class="b-main-content">
      <p>Create a new user by filling in the form below. Their account will be auto setup without a confirmation email.</p>
    </div>
    <table>
      <form id="addUser">
        <tr>
          <td>
            <label for="fname">First Name</label>
          <td>
          <td>
            <input id="fname" v-model="newUser.firstName" type="text" name="fname">
          </td>
        </tr>
        <tr>
          <td>
            <label for="lname">Last Name</label>
          <td>
          <td>
            <input id="lname" v-model="newUser.lastName" type="text" name="lname">
          </td>
        </tr>
        <tr>
          <td>
            <label for="email">Email</label>
          <td>
          <td>
            <input id="email" v-model="newUser.email" type="email" name="email">
          </td>
        </tr>
        <tr>
          <td>
            <label for="access">Access level</label>
          <td>
          <td>
            <input id="access" v-model="newUser.accessLevel" type="text" name="access">
          </td>
        </tr>
        <tr>
          <td>
            <label for="password">Password</label>
          <td>
          <td>
            <input id="password" v-model="newUser.password" type="password" name="password">
          </td>
        </tr>
        <tr>
          <td>
            <label for="confPassword">Confirm Password</label>
          <td>
          <td>
            <input id="confPassword" v-model="newUser.confPassword" type="password" name="confPassword">
          </td>
        </tr>
        <p>
          <input type="button" value="Submit" @click="checkForm()">
        </p>
      </form>
    </table>
  </b-container>
</template>

<script>
import { mapState } from 'vuex'
import { uuid } from 'vue-uuid'

export default {
    data: function() {
      return {
        newUser: {
          firstName: '',
          lastName: '',
          email: '',
          accessLevel: 0,
          password: '',
          confPassword: '',
          active: 1,
          username: ''
        }
      }
    },
    computed: {
        ...mapState({
            user: state => state.auth.user
        })
    },
    methods: {
      async checkForm() {
        if (this.newUser.password == this.newUser.confPassword){
          await this.$store.dispatch("auth/signUp", {
            username: this.generateUsername(),
            password: this.newUser.password,
            attributes: {
              name: this.newUser.firstName + ' ' + this.newUser.lastName,
              email: this.newUser.email
            }
          }).then(data => console.log(data)).catch(err => console.log(err))
        }
      },
      generateUsername() {
        return this.$uuid.v4()
      }
    }
}
</script>
