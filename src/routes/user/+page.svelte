<script>
  import ls from "localstorage-slim";
</script>

<div class="flex w-full flex-shrink-0 flex-col">
  <div class="mx-auto my-20 flex justify-center align-middle">
    <img
      class="h-40 rounded-full"
      src={`https://ui-avatars.com/api/?name=${ls.get(
        "username"
      )}&background=random`}
      alt="" />

    <h1
      class="text-slate-300 font-bold text-2xl font-poppins my-auto mx-10 text-center">
      {ls.get("username")}
    </h1>
  </div>

  <div>
    <a
      href="/"
      class="flex my-5 mx-auto font-poppins items-center bg-white border rounded-lg max-w-2xl shadow hover:bg-gray-100 border-gray-700 dark:bg-gray-700">
      <img
        class="object-cover rounded-l-lg h-32"
        src="https://image.tmdb.org/t/p/w200/dR1Ju50iudrOh3YgfwkAU1g2HZe.jpg"
        alt="" />
      <div
        class="flex justify-between w-full p-4 ml-4 divide-x-2 divide-slate-600">
        <h5 class="text-xl self-center font-bold tracking-wide text-slate-100 ">
          Ford vs. Ferrari
        </h5>
        <h5 class="text-slate-100 p-6 text-xl font-bold self-center">9.5</h5>
      </div>
    </a>
    <a
      href="/"
      class="flex my-5 mx-auto font-poppins items-center bg-white border rounded-lg max-w-2xl shadow hover:bg-gray-100 border-gray-700 dark:bg-gray-700">
      <img
        class="object-cover rounded-l-lg h-32"
        src="https://image.tmdb.org/t/p/w200/dR1Ju50iudrOh3YgfwkAU1g2HZe.jpg"
        alt="" />
      <div
        class="flex justify-between w-full p-4 ml-4 divide-x-2 divide-slate-600">
        <h5 class="text-xl self-center font-bold tracking-wide text-slate-300 ">
          Ford vs. Ferrari
        </h5>
        <h5 class="text-slate-200 p-6 text-xl font-bold self-center">9.5</h5>
      </div>
    </a>
    <a
      href="/"
      class="flex my-5 mx-auto font-poppins items-center bg-white border rounded-lg max-w-2xl shadow hover:bg-gray-100 border-gray-700 dark:bg-gray-700">
      <img
        class="object-cover rounded-l-lg h-32"
        src="https://image.tmdb.org/t/p/w200/dR1Ju50iudrOh3YgfwkAU1g2HZe.jpg"
        alt="" />
      <div
        class="flex justify-between w-full p-4 ml-4 divide-x-2 divide-slate-600">
        <h5 class="text-xl self-center font-bold tracking-wide text-slate-300 ">
          Ford vs. Ferrari
        </h5>
        <h5 class="text-slate-200 p-6 text-xl font-bold self-center">9.5</h5>
      </div>
    </a>
  </div>
</div>
