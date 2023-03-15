<script>
  import { Card, Button, Toggle } from "flowbite-svelte";
  let vCard = false;
</script>

<section class="dark:bg-gray-900 dark:text-gray-100">
  <div
    class="container flex flex-col justify-center p-6 mx-auto sm:py-12 lg:py-24 lg:flex-row lg:justify-between">
    <div
      class="flex flex-col justify-center p-6 text-center rounded-sm lg:max-w-md xl:max-w-lg lg:text-left">
      <p class="text-2xl font-bold font-['Open_Sans'] leading-none sm:text-6xl">
        Find Your<br />
        <span class="dark:text-violet-400"> Next </span> Movie Obsession
        <span class="dark:text-violet-400" />
      </p>
      <p class="mt-6 mb-8 text-lg sm:mb-12">
        Discover your next cinematic adventure with our
        <br class="hidden md:inline lg:hidden" />
        expertly curated movie recommendations
      </p>
    </div>
    <div
      class="flex items-center justify-center p-6 mt-8 lg:mt-0 h-72 sm:h-80 lg:h-96 xl:h-112 2xl:h-128">
      <img
        src="/hero3.svg"
        alt=""
        class="object-contain h-72 sm:h-80 lg:h-96 xl:h-112 2xl:h-128" />
    </div>
  </div>
</section>

<div
  class="w-60 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
  <a href="/">
    <img
      class="rounded-t-lg h-70"
      src="https://m.media-amazon.com/images/M/MV5BNjc0NGU1YjItZGIxZS00MjMxLTlmZmYtNWUyMWRmY2Y2NDA0XkEyXkFqcGdeQXVyMjUzOTY1NTc@._V1_SX300.jpg"
      alt="" />
  </a>
  <div class="p-2 text-center">
    <a href="/">
      <h5
        class="mb-2 text-lg font-bold  font-['Open_Sans'] tracking-tight text-gray-900 dark:text-white">
        Final Fantasy
      </h5>
    </a>
  </div>
</div>

<style>
  :global() {
    background: #111827;
  }
</style>
