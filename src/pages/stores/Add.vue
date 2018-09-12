/* eslint-disable */
<template>
  <b-container>
    <div class="b-main-content">
      <p>Please fill out the information pertaining to your store.</p>
      <table>
        <form id="addStore">
          <tr>
            <td>
              <label for="name">Store Name</label>
            <td>
            <td>
              <input id="name" v-model="store.name" type="text" name="name">
            </td>
          </tr>
          <tr>
            <td>
              <label for="address">Address</label>
            <td>
            <td>
              <input id="address" v-model="store.address" type="text" name="address">
            </td>
          </tr>
          <tr>
            <td>
              <label for="city">City</label>
            <td>
            <td>
              <input id="city" v-model="store.city" type="text" name="city">
            </td>
          </tr>
          <tr>
            <td>
              <label for="state">State</label>
            <td>
            <td>
              <input id="state" v-model="store.state" type="text" name="state">
            </td>
          </tr>
          <tr>
            <td>
              <label for="zip">Zipcode</label>
            <td>
            <td>
              <input id="zip" v-model="store.zip" type="text" name="zip">
            </td>
          </tr>
          <tr>
            <td>
              <label for="phone">Phone Number</label>
            <td>
            <td>
              <input id="phone" v-model="store.phone" type="text" name="phone">
            </td>
          </tr>
          <p>
            <input type="button" value="Submit" @click="checkForm()">
          </p>
        </form>
      </table>
    </div>
  </b-container>
</template>

<script>
import { mapState } from 'vuex'

export default {
    data: function () {
      return {
        store: {
          name: '',
          address: '',
          city: '',
          state: '',
          zip: '',
          phone: ''
        }
      }
    },
    computed: {
        ...mapState({
            user: state => state.auth.user
        })
    },
    methods: {
        // Validate form
        checkForm() {

        },
        // Insert to db as the userId as store Owner
        addStore() {

        }
    }
}
</script>
