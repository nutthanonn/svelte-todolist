<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let title;
  let detail;

  const handleSubmit = () => {
    const todo = { title, detail, id: Math.random() };
    dispatch("addTodo", todo);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <div class="title">
    <label for="title">Title: </label>
    <input type="text" bind:value={title} id="title" />
  </div>
  <div class="detail">
    <label for="detail">Detail: </label>
    <input type="text" bind:value={detail} id="detail" />
  </div>
  <button>Add new todo</button>
</form>

<style>
  form {
    width: 500px;
    margin: 0 auto;
    text-align: center;
  }
  label {
    color: gray;
    margin: 10px;
    font-size: 20px;
    text-align: left;
  }
  input {
    border-radius: 5px;
    width: 100%;
  }
  button {
    margin-top: 5px;
  }
</style>
