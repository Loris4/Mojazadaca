<template>
  <div class="home">
    Ja sam varijabla ali sam pretvoren u string
    <br />
    <br />
    <br />
    <br />

    <ul>
      <li v-for="item in commits" v-bind:key="item.sha">
        Commit 
        <router-link :to="'/commit/' + item.sha">{{ item.sha }}</router-link>
        <router-link :to="{name: 'about', params: {sha: item.sha}}">{{ item.sha }}</router-link>
          item.sha
      </li>
    </ul>
  </div>
</template>

<script>

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
