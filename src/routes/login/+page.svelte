<script>
  import { Card, Button, Label, Input, Checkbox } from "flowbite-svelte";
  import ls from "localstorage-slim";
  // 43200
  let username = "";
  let password = "";

  let login = true;
  const toggle_login = () => {
    login = !login;
    (username = ""), (password = "");
  };
  const signin = async () => {
    let res = await fetch("http://localhost:8000/api/token/", {
      method: "POST",
      body: JSON.stringify({ username: username, password: password }),
      headers: {
        "Content-Type": "application/json",
      },
    });
    let token = await res.json();
    if (res.ok) {
      console.log(token);
      ls.set("jwt", token.access, { ttl: 43200 });
      // @ts-ignore
      window.location = "/";
    } else {
      console.log(token.detail);
      if (token.username) console.log("username: " + token.username[0]);
      if (token.password) console.log("password: " + token.password[0]);
      ls.clear();
    }
    (username = ""), (password = "");
  };
  const signup = async () => {
    let res = await fetch("http://localhost:8000/user/create/", {
      method: "POST",
      body: JSON.stringify({ username: username, password: password }),
      headers: {
        "Content-Type": "application/json",
      },
    });
    let token = await res.json();
    if (Object.keys(token).length === 0) {
      console.log("successfully created user");
      toggle_login();
    } else console.log("failed to create user");
  };
  const signout = () => {
    ls.clear();
  };
</script>

<!-- {#if login} -->
<!-- <h1>signin</h1> -->
<!-- <input type="text" placeholder="Username" bind:value={username} /> -->
<!-- <input type="password" placeholder="Password" bind:value={password} /> -->
<!-- <button on:click={signin}>signin</button> -->
<!-- <p>Don't have Account?</p> -->
<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- <p on:click={toggle_login}>Signup</p> -->
<!-- {:else} -->
<!-- <h1>signup</h1> -->
<!-- <input type="text" placeholder="Username" bind:value={username} />
    <input type="password" placeholder="Password" bind:value={password} />
    <button on:click={signup}>signup</button>
    <p>Already have Account?</p>
    svelte-ignore a11y-click-events-have-key-events
    <p on:click={toggle_login}>Signin</p> -->
<!-- {/if} -->

<!-- <div>
    <button on:click={signout}>signout</button>
</div> -->
{#if login}
  <!-- signin -->
  <div class="grid h-screen place-items-center bg-gray-900">
    <div class="w-96">
      <Card>
        <form class="flex flex-col space-y-6" action="/">
          <h3 class="text-xl font-medium text-gray-900 dark:text-white p-0">
            Sign in to our platform
          </h3>
          <Label class="space-y-2">
            <span>Username</span>
            <Input
              bind:value={username}
              type="text"
              name="email"
              placeholder="xyz123"
              required />
          </Label>
          <Label class="space-y-2">
            <span>Your password</span>
            <Input
              bind:value={password}
              type="password"
              name="password"
              placeholder="•••••"
              required />
          </Label>
          <Button on:click={signin} class="w-full"
            >Login to your account</Button>
          <div class="text-sm font-medium text-gray-500 dark:text-gray-300">
            Not registered? <span
              on:click={toggle_login}
              class="text-blue-700 hover:underline dark:text-blue-500"
              >Create account</span>
          </div>
        </form>
      </Card>
    </div>
  </div>
{:else}
  <div class="grid  h-screen place-items-center bg-gray-900">
    <div class="w-96">
      <Card>
        <form class="flex flex-col space-y-6" action="/">
          <h3 class="text-xl font-medium text-gray-900 dark:text-white p-0">
            Create a new account
          </h3>
          <Label class="space-y-2">
            <span>Username</span>
            <Input
              bind:value={username}
              type="text"
              name="email"
              placeholder="xyz123"
              required />
          </Label>
          <Label class="space-y-2">
            <span>Your password</span>
            <Input
              bind:value={password}
              type="password"
              name="password"
              placeholder="•••••"
              required />
          </Label>
          <Button on:click={signup} class="w-full">Create Account</Button>
          <div class="text-sm font-medium text-gray-500 dark:text-gray-300">
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            Already have an account?
            <span
              on:click={toggle_login}
              class="text-blue-700 hover:underline dark:text-blue-500">
              Sign in</span>
          </div>
        </form>
      </Card>
    </div>
  </div>
{/if}
