<script>
  import { createEventDispatcher } from "svelte";
  import { fade } from "svelte/transition";
  import { flip } from "svelte/animate";
  const dispatch = createEventDispatcher();

  export let todo = [];

  const handleClick = (id) => {
    dispatch("del", id);
  };
</script>

<div class="container">
  {#each todo as item (item.id)}
    <div class="card" animate:flip={{ duration: 300 }} in:fade>
      <p class="title">
        <strong>{item.title}</strong>
      </p>
      <div class="detail">
        {item.detail}
      </div>
      <button on:click={() => handleClick(item.id)}>Delete</button>
    </div>
  {/each}
</div>

<style>
  .container {
    width: 700px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
  }
  .card {
    max-height: fit-content;
    min-width: 160px;
    padding: 10px 30px;
    border-radius: 10px;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
  }
  .title {
    font-size: large;
    color: rgb(89, 117, 241);
  }
  .detail {
    max-height: fit-content;
    max-width: min-content;
    color: gray;
  }
  button {
    margin-top: 10px;
    border: 0;
    cursor: pointer;
    box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
  }
</style>
