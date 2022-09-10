<template>

  <div class="user-profile">
      <div class="user-profile__user-panel">

        <h1 class="user-profile__">@{{ user.username }}</h1>

        <div class="user-profile__admin-badge" v-if="user.isAdmin">
            Admin
        </div>

        <div class="user-profile__follower-count">
          <strong>Followers: </strong> {{ followers }}
        </div>

      </div>

      <div class="user-profile__twoots-wrapper">
        <TwootItem
            v-for="twoot in user.twoots"
            :key="twoot.id"
            :username="user.username"
            :twoot="twoot"
            @favorite="toggleFavorite"
        />
      </div>

    </div>

</template>


<script>
import TwootItem from "./TwootItem.vue";

export default {
    name: "UserProfile",
    components: { TwootItem },

    data() {
        return {
            followers: 0,
            user: {
                id: 1,
                username: "carla-test",
                firstName: "Carla",
                lastName: "N",
                email: "test@test.com",
                isAdmin: true,
                twoots: [
                    { id: 1, content: "Twooter is amazing!" },
                    { id: 2, content: "Don't forget to subscribe!" }
                ]
            }
        };
    },

    watch: {
        followers(newFollowerCount, oldFollowerCount) {
            if (oldFollowerCount < newFollowerCount) {
                console.log(`${this.user.username} has gained a follower!`);
            }
        }
    },

    computed: {
        fullName() {
            return `${this.user.firstName} ${this.user.lastName}`;
        }
    },

    methods: {
        followUser() {
            this.followers++;
        },
        toggleFavorite( id ) {
            console.log(`Favorited twoot #${id}`)
        }
    },

    mounted() {
        this.followUser();
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

.user-profile__admin-badge {
    background: rebeccapurple;
    border-radius: 5px;
    color: #FFF;
    font-size: 12px;
    font-weight: bold;
    letter-spacing: 1.1px;
    margin-right: auto;
    padding: 2px 10px;
}

h1 {
    margin: 0;
}

</style>