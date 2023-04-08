<script>
  // @ts-nocheck
  import Moviecard from "$lib/moviecard.svelte";
  import ls from "localstorage-slim";
  import { onMount } from "svelte";
  import { djangoapi } from "../../app/stores";

  let currpage = 0;
  let totalmovie = Array();
  let currmovie = [];
  const loadmovie = async () => {
    let headers = {};
    if (ls.get("jwt") != null)
      headers = { Authorization: `Bearer ${ls.get("jwt")}` };
    let res = await fetch(`${$djangoapi}/user/home/`, { headers });
    let data = await res.json();
    totalmovie = data;
    console.log(typeof totalmovie[0]);
  };
  $: currmovie = totalmovie.slice(currpage * 10, currpage * 10 + 10);

  onMount(loadmovie);
</script>

<div class="flex flex-wrap px-10 justify-evenly">
  {#each currmovie as movie}
    <Moviecard
      poster={movie.Poster_path}
      imdb_id={movie.Imdb_id}
      name={movie.Title} />
  {/each}
</div>

<nav aria-label="Page navigation example" class="flex justify-center p-5">
  <ul class="inline-flex items-center -space-x-px">
    <li>
      <button
        on:click={() => {
          currpage = 0;
        }}
        class="px-3 py-2 leading-tight rounded-l-xl border bg-gray-800 border-gray-700 text-gray-400 hover:bg-gray-700 hover:text-white btn"
        class:active={currpage === 0}>1</button>
    </li>
    <li>
      <button
        on:click={() => {
          currpage = 1;
        }}
        class="px-3 py-2 leading-tight border bg-gray-800 border-gray-700 text-gray-400 hover:bg-gray-700 hover:text-white btn"
        class:active={currpage === 1}>2</button>
    </li>
    <li>
      <button
        on:click={() => {
          currpage = 2;
          console.log(currpage);
        }}
        class=" px-3 py-2 leading-tight border rounded-r-xl bg-gray-800 border-gray-700 text-gray-400 hover:bg-gray-700 hover:text-white btn active"
        class:active={currpage === 2}>3</button>
    </li>
  </ul>
</nav>

<style>
  .active {
    background-color: #374151;
  }
</style>
