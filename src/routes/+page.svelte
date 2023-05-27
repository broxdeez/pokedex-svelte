<script>
    import { generations } from "./generations";
    export let data;
</script>

<div class="generations">
    {#each generations as generation}
        <div class="generation">{generation.main_region}</div>
    {/each}
</div>

<div class="monsters">
    {#each data.monsters as monster (monster.id)}
        <div class="monster">
            <div class="monster-content">
                <img src={monster.image} alt={monster.name} />
                {monster.name}
            </div>
            <div class="monster-id">
                {monster.id}
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
        border : 1px solid black;
        background-color:beige;
        color: #333;
    }
    .generation:hover{
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
