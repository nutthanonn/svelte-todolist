<script>
  import Header from "./components/header.svelte";
  import Footer from "./components/footer.svelte";
  import Tabs from "./shared/Tabs.svelte";
  import Form from "./components/formTodolist.svelte";
  import TodoList from "./components/todoList.svelte";

  let items = ["Current Todo", "Add New Todo"];
  let activeItem = "Current Todo";

  const changeTabs = (e) => {
    activeItem = e.detail;
  };

  let todo = [
    {
      id: 1,
      title: "Code",
      detail: "Workkk",
    },
    {
      id: 12,
      title: "Code",
      detail: "Workkk",
    },
    {
      id: 13,
      title: "Code",
      detail: "Workkk",
    },
    {
      id: 14,
      title: "Code",
      detail: "Workkk",
    },
    {
      id: 15,
      title: "Code",
      detail: "Workkk",
    },
    {
      id: 16,
      title: "Code",
      detail: "Workkk",
    },
  ];

  const addTodo = (e) => {
    activeItem = "Current Todo";
    todo = [e.detail, ...todo];
  };

  const delTodo = (e) => {
    todo = todo.filter((item) => item.id != e.detail);
  };
</script>

<Header />
<main>
  <Tabs {activeItem} {items} on:changeTabs={changeTabs} />
  {#if activeItem === "Current Todo"}
    <TodoList {todo} on:del={delTodo} />
  {:else if activeItem === "Add New Todo"}
    <Form on:addTodo={addTodo} />
  {/if}
</main>
<Footer />

<style>
  main {
    margin: 30px auto;
    max-width: 960px;
  }
</style>
