<script>
  export let link = "";
  export let name = "";
</script>

<div class="w-fit m-6 border rounded-md shadow bg-gray-700 border-gray-800">
  <div class="">
    <a href="/">
      <img class="rounded-t-md h-72 w-48" src={link} alt="" />
    </a>
  </div>
  <div class="flex flex-col p-2 text-center justify-end">
    <a href="/">
      <h5
        class="w-44 mb-2 text-lg font-bold font-poppins tracking-tight text-slate-300">
        {name}
      </h5>
    </a>
  </div>
</div>
