<template>

  <div class="user-profile">
      <div class="user-profile__user-panel">
        <h1 class="user-profile__">@{{ user.username }}</h1>
        <div class="user-profile__follower-count">
          <strong>Followers: </strong> {{ followers }}
        </div>
      </div>
    </div>

</template>

<script>
export default {
  name: 'UserProfile',

  data() {

    return {
      followers: 0,
      user: {
        id: 1,
        username: 'carla-test',
        firstName: 'Carla',
        lastName: 'N',
        email: 'test@test.com',
        isAdmin: true
      }
    }

  },

  watch: {

    followers( newFollowerCount, oldFollowerCount ) {
      if ( oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`)
      }
    }

  },

  computed: {

    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    }

  },

  methods: {

    followUser() {
      this.followers++
    }

  },

  mounted() {
    this.followUser()
  }

}
</script>

<style>
.user-profile {
    display: grid;
    grid-gap: 50px;
    grid-template-columns: 1fr 3fr;
    padding: 50px 5%;
}

.user-profile__user-panel {
    background-color: white;
    border-radius: 5px;
    border: 1px solid #DFE3E8;
    margin-bottom: auto;
    padding: 20px;

    display: flex;
    flex-direction: column;
}

h1 {
      margin: 0;
    }

</style>