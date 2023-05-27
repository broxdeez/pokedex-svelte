<script>
    import { generations } from "./generations";
    export let data;
</script>

{#each data.monsters as monster (monster.id)}
    <p>{monster.id} : {monster.name}</p>
{/each}

{#each generations as generation}
    <p>{generation.name}</p>
    <p>Main Region : {generation.main_region}</p>
    <p>Games : {generation.games.join(", ")}</p>
{/each}

<style>
</style>
