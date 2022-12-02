<script>
    // transition directives for the table and items as they are added/removed
    import { fly, fade } from 'svelte/transition';
    // animation directive for items as they are repositioned
    import { flip } from 'svelte/animate';

    // use the data received from the parent component to create a table highlighting the words and frequencies in table rows
    export let data;
</script>

<!-- transition the section from the left -->
<section class="spreadsheet" transition:fly={{ x: -25 }}>
    <svg class="icon" viewBox="0 0 90 100" width="45" height="50">
        <use href="#table" />
    </svg>
    <table>
        <tr>
            <th>Word</th>
            <th>Frequency</th>
        </tr>
        <!-- for each object include a row with two cells, describing the word and frequency
            it is possible to use the word as a key as this is a unique value
            transition new rows from the left
            animate existing rows through the flip animation
            -->
        {#each data as datum (datum.word)}
            <tr in:fly={{ x: -50 }} animate:flip>
                <td>{datum.word}</td>
                <td class="number">{datum.frequency}</td>
            </tr>
        {/each}
    </table>
</section>

<style>

</style>
