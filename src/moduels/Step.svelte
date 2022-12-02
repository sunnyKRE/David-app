<script>
    export let steps;
    export let level;
    export let color;
    export let margin;

</script>
<div class="step">
    {#each steps as step ,index}
        <div class="step__cover__text">{step}</div>
    {/each}
</div>

<div class="step">
    {#each steps as step ,index}
        {#if level <= index}
        <div class="step__line active {color}"></div>
        <div class="step__cover">
            <div class="step__cover__circle active {color}"></div>
        </div>

        {:else}
        <div class="step__line {color}" ></div>
        <div class="step__cover">
            <div class="step__cover__circle {color}"></div>
        </div>
<!--        <div class="step__cover">-->
<!--            <div class="step__cover__text">{step}</div>-->
<!--        </div>-->
        {/if}
    {/each}
</div>


<style>
    /*.step {*/
    /*    width: 100%;*/
    /*    position: relative;*/
    /*    display: flex;*/
    /*    align-items: center;*/
    /*}*/

    /*.step__cover {*/
    /*    display: flex;*/
    /*    flex-direction: column;*/
    /*    align-items: center;*/
    /*}*/

    /*.step__cover__circle {*/
    /*    width: 40px;*/
    /*    height: 40px;*/
    /*    line-height: 40px;*/
    /*    border-radius: 100%;*/
    /*    border: 1px solid #0d6efd;*/
    /*    background-color: #0d6efd;*/
    /*    color: #fff;*/
    /*    z-index: 100;*/
    /*}*/
    /*.step__cover__circle.active {*/
    /*    border: 1px solid #6c757d;*/
    /*    background-color: #6c757d;*/
    /*}*/

    /*.step__line {*/
    /*    width: 20%;*/
    /*    height: 4px;*/
    /*    background-color: #0d6efd;*/
    /*    margin-bottom: 22px;*/
    /*}*/

    /*.step__line.active{*/
    /*    background-color: #6c757d;*/
    /*}*/

    /*.step__line:first-child {*/
    /*   display: none;*/
    /*}*/
</style>
