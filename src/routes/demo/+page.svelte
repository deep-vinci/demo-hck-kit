<script>
    import { onMount } from 'svelte';
  
    let data;
  
    onMount(async () => {
      const response = await fetch('https://catfact.ninja/fact');
      if (response.ok) {
        data = await response.json();
      } else {
        console.error('Failed to fetch data');
      }
    });
  </script>
  
  <main>
    <h1>Fetched Data (Client-Side)</h1>
    {#if data}
      <p>{data.fact}</p>
    {/if}
  </main>
  
<!-- <script context="module">
  export async function load() {
    let response = await fetch("https://catfact.ninja/fact");
    let data = await response.json()

    console.log(data)

    return {
      props: {
        message: "This is loaded data!",
      },
    };
  }
</script>

<h1>Welcome to Demo</h1>
<p>
  Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation
</p> -->
