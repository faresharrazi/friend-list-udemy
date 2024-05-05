<template>
  <section>
    <h1>Friend List</h1>
    <ul>
      <friend-contact></friend-contact>
      <friend-contact></friend-contact>
      <friend-contact></friend-contact>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: "Hou",
          name: "Houssam",
          email: "Samsam@yahoo.ca",
        },
        {
          id: "Sani",
          name: "Yassine",
          email: "Baim@yahoo.gr",
        },
      ],
    };
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
