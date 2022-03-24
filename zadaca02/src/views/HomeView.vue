<template>
  <div class="home">Prazna</div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  data: function() {
    return {
      ime: "Loris",
      prezime: "Lukić",
      commits: [],
    };
  },
  async mounted() {
    let rezultat = await fetch("https://api.github.com/repos/vuejs/vue/commits");
    
    let podaci = await rezultat.json();

    for (let item of podaci) {
      console.log(item[item.sha]);
    }
    alert(this.ime)
    this.commits = podaci;
  },
};
</script>
