<script>
  import { onMount } from "svelte";
  import BridgeNotify from "bridge-svelte";
  import { notify } from "bridge-svelte";
  let type = "success";
  let duration = 3000;
  let message = "Bridge Notification is Awesome 😍";
  let animate = {
    y: 100,
    x: 0,
    duration: 500
  };
  let style = null;
  function show(position) {
    notify({
      message: message,
      type: type,
      style: style,
      duration: duration,
      position: position,
      animate: animate
    });
  }
</script>

<main>
  <BridgeNotify />
  <div class="flex justify-center p-20">
    <div class="w-8/12">
      <h1 class="text-5xl w-full text-center">Bridge Notification</h1>

      <div class="flex justify-between py-5">
        <button
          class="px-2 py-3 border border-gray-400 rounded-md shadow-md w-32
          text-center mx-1"
          on:click={() => show('left')}>
          Left
        </button>
        <button
          class="px-2 py-3 border border-gray-400 rounded-md shadow-md w-32
          text-center mx-1"
          on:click={() => show('center')}>
          Center
        </button>
        <button
          class="px-2 py-3 border border-gray-400 rounded-md shadow-md w-32
          text-center mx-1"
          on:click={() => show('right')}>
          Right
        </button>
        <button
          class="px-2 py-3 border border-gray-400 rounded-md shadow-md w-32
          text-center mx-1"
          on:click={() => show('left bottom')}>
          Bottom Left
        </button>
        <button
          class="px-2 py-3 border border-gray-400 rounded-md shadow-md w-32
          text-center mx-1"
          on:click={() => show('center bottom')}>
          Bottom Center
        </button>
        <button
          class="px-2 py-3 border border-gray-400 rounded-md shadow-md w-32
          text-center mx-1"
          on:click={() => show('bottom right')}>
          Bottom Right
        </button>
      </div>

      <div class="flex justify-between py-3 my-5 border rounded shadow">
        <div class="w-7/12">
          <input
            type="text"
            class="border border-gray-300 rounded-md p-2 mx-3 w-full"
            bind:value={message} />
        </div>
        <div class="">
          <label class="p-4 text-center">
            Remove After (in ms)
            <input
              type="number"
              class="border border-gray-300 rounded-md shadow p-2 mx-3"
              bind:value={duration}
              min="500"
              max="100000"
              step="100" />
          </label>
        </div>
      </div>

      <div
        class="flex justify-between py-3 my-5 font-semibold border rounded
        shadow">
        <label class="p-2 text-center">
          Success
          <input type="radio" bind:group={type} value="success" />
        </label>
        <label class="p-2 text-center">
          Error
          <input type="radio" bind:group={type} value="error" />
        </label>
        <label class="p-2 text-center">
          Warning
          <input type="radio" bind:group={type} value="warning" />
        </label>
        <label class="p-2 text-center">
          Info
          <input type="radio" bind:group={type} value="info" />
        </label>
        <label class="p-2 text-center">
          Normal
          <input type="radio" bind:group={type} value="normal" />
        </label>
      </div>

      <div
        class="flex justify-between py-3 my-5 font-semibold border rounded
        shadow">
        <div class="flex">
          <p class="p-2">Animation X position</p>
          <input
            type="number"
            class="border border-gray-300 rounded-md shadow px-2 py-1 mx-3"
            bind:value={animate.x}
            min="0"
            max="1000"
            step="100" />
        </div>
        <div class="flex">
          <p class="py-2">Animation Y position</p>
          <input
            type="number"
            class="border border-gray-300 rounded-md shadow p-2 mx-3"
            bind:value={animate.y}
            min="0"
            max="1000"
            step="100" />
        </div>
        <div class="flex">
          <p class="py-2">Animation Duration</p>
          <input
            type="number"
            class="border border-gray-300 rounded-md shadow p-2 mx-3"
            bind:value={animate.duration}
            min="0"
            max={duration}
            step="100" />
        </div>
      </div>

      <div
        class="flex justify-between p-3 my-5 font-semibold border rounded shadow">
        <div class="flex w-full">
          <p class="p-2 w-3/12">Writing Custom Style</p>
          <textarea bind:value={style} class="border w-full rounded" />
        </div>
      </div>
    </div>
  </div>
</main>
