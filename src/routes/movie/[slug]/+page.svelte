<script>
  import Crewcard from "$lib/crewcard.svelte";
  import { onMount } from "svelte";
  export let data;
  let movieinfo = {
    backdrop: "https://image.tmdb.org/t/p/original",
    poster: "https://image.tmdb.org/t/p/w300",
    title: "",
    year: "",
    tagline: "",
    overview: "",
  };
  // @ts-ignore
  /**
   * @type {any[]}
   */
  let cast = [];
  // @ts-ignore
  let director = { name: "", profile_path: "" };
  const loadmovie = async () => {
    let res = await fetch(
      `https://api.themoviedb.org/3/movie/${data.slug}?api_key=843811a4e70cd56397b52a070f1ddf61`
    );
    let info = await res.json();
    if (info) {
      movieinfo.poster += info["poster_path"];
      movieinfo.backdrop += info["backdrop_path"];
      movieinfo.title = info["original_title"];
      movieinfo.overview = info["overview"];
      movieinfo.tagline = info["tagline"];
      movieinfo.year = info["release_date"].slice(0, 4);
    }
  };
  const loadcast = async () => {
    let res = await fetch(
      `https://api.themoviedb.org/3/movie/${data.slug}/credits?api_key=843811a4e70cd56397b52a070f1ddf61`
    );
    let info = await res.json();
    for (let i = 0; i < info["crew"].length; i++) {
      if (info["crew"][i]["job"] === "Director") {
        director = info["crew"][i];
      }
    }
    cast = info["cast"].slice(0, 5);
  };

  onMount(async () => {
    Promise.all([loadcast(), loadmovie()]);
  });
</script>

<div class="relative">
  <!-- image -->
  <!-- bg-[url('https://image.tmdb.org/t/p/w500/pbEkjhdfP7yuDcMB78YEZwgD4IN.jpg')] -->
  <div
    class=" w-full h-[38rem] bg-no-repeat bg-cover"
    style="background-position-y: 50%; background-image: linear-gradient(rgba(30, 41, 59, 0.6),rgba(30, 41, 59, 0.7)), url({movieinfo.backdrop})" />
  <!-- content -->
  <div class="absolute top-0 flex py-10 px-28 h-[38rem]">
    <div class="flex-shrink-0 self-center">
      <img src={movieinfo.poster} alt="" class="rounded-xl" />
    </div>
    <div class="text-white p-10 self-center font-poppins">
      <p class="text-4xl my-5 font-extrabold">
        {movieinfo.title} <span class="text-slate-300">({movieinfo.year})</span>
      </p>
      <p class="italic text-slate-300">{movieinfo.tagline}</p>
      <p class="my-3 text-xl font-semibold">Overview</p>
      <p class="">{movieinfo.overview}</p>
    </div>
  </div>
</div>

<div
  class="flex px-5 py-10 divide-x-2 divide-slate-600 justify-center font-poppins">
  <!-- director -->
  <div class="pr-3">
    <p class="text-slate-300 m-5 text-xl">Director</p>
    <Crewcard
      link={"https://image.tmdb.org/t/p/w300/" + director["profile_path"]}
      name={director["name"]} />
  </div>
  <!-- crew -->
  <div class="pl-3">
    <p class="text-slate-300 m-5 text-xl">Cast</p>
    <div class="flex flex-wrap">
      {#each cast as person}
        <Crewcard
          link={"https://image.tmdb.org/t/p/w300/" + person["profile_path"]}
          name={person["name"]} />
      {/each}
    </div>
  </div>
</div>
