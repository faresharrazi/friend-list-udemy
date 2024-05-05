<template>
  <section>
    <h1>Friend List</h1>
    <ul>
      <friend-contact
        v-for="f in friends"
        :name="f.name"
        :email="f.email"
        :phone="f.phone"
        :key="f.id"
      ></friend-contact>
    </ul>
    <button @click="toggleAddNewContact">
      {{ !addNewContact ? "+" : "cancel" }}
    </button>
    <div v-if="addNewContact">
      <input type="text" placeholder="name" v-model="newFriend.name" />
      <input type="text" placeholder="email" v-model="newFriend.email" />
      <input type="text" placeholder="phone" v-model="newFriend.phone" />
      <button type="submit" @click.prevent="addNewFriend">Add</button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      addNewContact: false,
      newFriend: {
        name: "",
        email: "",
        phone: "",
      },
      friends: [
        {
          id: "Hou",
          name: "Houssam Bounasri",
          email: "Samsam@yahoo.ca",
          phone: "22 546 123",
        },
        {
          id: "Sani",
          name: "Yassine Sghir",
          email: "Baim@yahoo.gr",
          phone: "22 512 052",
        },
        {
          id: "Lee",
          name: "Ali Fathallah",
          email: "Lee@yahoo.fr",
          phone: "98 216 256",
        },
      ],
    };
  },
  methods: {
    toggleAddNewContact() {
      this.addNewContact = !this.addNewContact;
    },

    addNewFriend() {
      this.friends.push({
        id: this.newFriend.name,
        name: this.newFriend.name,
        email: this.newFriend.email,
        phone: this.newFriend.phone,
      });
      this.newFriend.name = "";
      this.newFriend.email = "";
      this.newFriend.phone = "";
      this.addNewContact = false;
    },
  },
};
</script>

<style scoped>
h1 {
  width: 500px;
  text-align: center;
  border: 2px solid black;
  color: aliceblue;
  background-color: brown;
}
section {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
