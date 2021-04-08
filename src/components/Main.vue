<template>
  <main>
    <h1>Rick and Morty</h1>
    <div class="container mt-4" v-if="personajes.length > 0">
      <div class="row">
        <div class="col-12 mb-4 rickmor" v-for="(rickmorty, i) in personajes" :key="i">
          <img :src="rickmorty.image" class="img-rick" alt="rickmorty" />
          <h5 class="card-title text-capitalize">{{ rickmorty.name }}</h5>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Main",
  data() {
    return {
      personajes: [],
      };
  },
  mounted(){
    this.getData ();
  },
  methods: {
    async getData() {
      const url = "https://rickandmortyapi.com/api/character";
      try {
        const req = await fetch(url);
        const reqJSON = await req.json();
        this.personajes = reqJSON.results;
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
h1 {
  color: #fff;
  font-weight: bold;
  font-size: 50px;
}
.rickmor{
  display: flex;
  align-items: center;
}
.img-rick{
  width: 10%;
  border-radius: 50%;
  margin-right: 15px;
}
h5{
  color: #68AB41;
  font-weight: bold;
}

</style>
