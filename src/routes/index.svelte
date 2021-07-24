<script>
  import { onMount } from "svelte";
  let QrCode;
  onMount(async () => {
    QrCode = (await import("https://cdn.jsdelivr.net/npm/svelte-qrcode"))
      .default;
  });
</script>

{#await QrCode}
  <p>...waiting</p>
{:then component}
  <svelte:component this={component} value="123" />
{:catch error}
  <p style="color: red">{error.message}</p>
{/await}
