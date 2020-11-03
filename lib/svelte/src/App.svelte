<script lang="ts">
  import ListItem from "./ListItem.svelte";
  import type { ListItemModel } from "./types";

  export let title: string = "Simple List";
  export let currentValue: string = "";
  let items: ListItemModel[] = [];
  const addItem = () => {
    items.push({ title: currentValue, index: items.length });
    items = items;
    currentValue = "";
  };

  const updateValue = (
    e: Event & {
      currentTarget: EventTarget & HTMLInputElement;
    }
  ) => {
    e.preventDefault();
    currentValue = e.currentTarget.value;
  };

  const removeItem = (index: number) => {
    items.splice(index, 1);
    items = items;
  };
</script>

<style>
  .list-wrapper {
    display: flex;
    flex-direction: column;
  }
</style>

<main>
  <h1>{title}</h1>
  <div>
    <input on:change={updateValue} value={currentValue} />
    <button on:click={addItem}> Add Item </button>
  </div>

  <div class="list-wrapper">
    {#each items as item}
      <ListItem listItem={item} onDeleteItem={removeItem} />
    {/each}
  </div>
</main>
