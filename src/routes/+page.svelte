<script>
    import { generations } from "./generations";
    import { page } from "$app/stores";
    import { goto } from "$app/navigation";
    export let data;
    $: monsterId = $page.url.searchParams.get("monsterId");
    $: monster = data.monsters.find((monster) => monster.id === monsterId)
    $: monsterId2 = $page.url.searchParams.get("monsterId2") || '';
    $: monster2 = data.monsters.find((monster) => monster.id === monsterId2);
    const updateSearchParams = (key, value) => {
    const searchParams = new URLSearchParams($page.url.searchParams);
    searchParams.set(key, value);
    goto(`?${searchParams.toString()}`);
    };
</script>

<h1>{monsterId}</h1>
<h2>{monster?.name}</h2>
<h1>{monsterId2}</h1>
<h2>{monster2?.name}</h2>

<div class="generations">
    {#each generations as generation}
        <div class="generation">{generation.main_region}</div>
    {/each}
</div>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="monsters">
    {#each data.monsters as monster (monster.id)}
    <div class="monster">
        <div on:click={() => updateSearchParams('monsterId', monster.id)}>
          <div class="monster-content">
            <img src={monster.image} alt={monster.name} />
            {monster.name}
          </div>
          <div class="monster-id">
            {monster.id}
          </div>
        </div>
        <div on:click={() => updateSearchParams('monsterId2', monster.id)}>
            Add Monster 2
          </div>
        </div>
    {/each}
</div>

<style>
    .generations {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: center;
    }
    .generation {
        margin: 5px;
        padding: 5px 10px;
        border: 1px solid black;
        background-color: beige;
        color: #333;
    }
    .generation:hover {
        background-color: #eee;
    }
    .monsters {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: center;
    }
    .monster {
        width: 100px;
        margin: 10px;
        padding: 10px;
        position: relative;
        background-color: #eee;
    }
    .monster:hover {
        background-color: #ddd;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    }
    .monster-content {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .monster-id {
        position: absolute;
        top: 8px;
        font-size: 0.8em;
        color: #aaa;
    }
</style>
