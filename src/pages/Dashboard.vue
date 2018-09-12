<template>
  <b-container>
    <div class="b-main-content">
      <p>To get started please add a store.</p>
      <button
        class="nav-btn"
        @click="add_store()">
        Add Store
      </button>
    </div>
  </b-container>
</template>

<script>
import { mapState } from 'vuex'

export default {
    computed: {
        ...mapState({
            user: state => state.auth.user,
        })
    },
    methods: {
      add_store(){
        this.$router.push('/addStore')
      }
    }
}
</script>
