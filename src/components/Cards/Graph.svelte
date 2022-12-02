<script>


    import {onMount} from 'svelte';
    import { draw, fade } from 'svelte/transition';

    import { extent } from 'd3-array';
    import { scaleLinear } from 'd3-scale';
    import { line, curveBasis } from 'd3-shape';
    import data2 from "./data2"
    import data1 from "./data"


    // the props
    let data1_t = data1;
    let data2_t = data2;
    let index;
    export let steps;
    export let level;
    let xScale_1;
    let yScale_1;
    let pathLine_1;
    let lineTest_1;
    let xScale_2;
    let yScale_2;
    let pathLine_2;
    let lineTest_2;

    // the scales

    xScale_1 = scaleLinear()
        .domain(extent(data1.map(d => d.valueX)))
        .range([0, 150]);

    yScale_1 = scaleLinear()
        .domain(extent(data1.map(d => d.valueY)))
        .range([25, 25]);



    xScale_2 = scaleLinear()
        .domain(extent(data2.map(d => d.valueX)))
        .range([0, 150]);

    yScale_2 = scaleLinear()
        .domain(extent(data2.map(d => d.valueY)))
        .range([5, 25]);








    // the path generator
    pathLine_1 = line()
        .x(d => xScale_1(d.valueX))
        .y(d => yScale_1(d.valueY))
        .curve(curveBasis)

    lineTest_1 = line()
        .x(d => xScale_1(d.valueX))
        .y(d => yScale_1(d.valueY))


    // the path generator
    pathLine_2 = line()
        .x(d => xScale_2(d.valueX))
        .y(d => yScale_2(d.valueY))
        .curve(curveBasis)

    lineTest_2 = line()
        .x(d => xScale_2(d.valueX))
        .y(d => yScale_2(d.valueY))




</script>
<div style="display: flex; margin:0 10%; height: 50px; align-items: center;">
    <div style="display: flex; height: 50px; align-items: center; flex-grow: 3">

        {#each steps as step ,index}
            {#if level <= index}
                {#if level === index}
                    <div class="step__cover">
                        <div class="step__cover__circle waiting">
                            <div class="step__cover__circle waiting inner"></div>
                        </div>
                    </div>
                {:else}
                    <div class="step__cover">
                        <div class="step__cover__circle"></div>
                    </div>
                {/if}
                <svg viewBox="0 0 150 50" class="line">
                    <path d={pathLine_1(data1)} class="path_part1"/>
                </svg>
            {:else}
                <div class="step__cover">
                    <div class="step__cover__circle active"></div>
                </div>
                <svg viewBox="0 0 150 50" class="line">
                    <path class="path_part1 c2" d={pathLine_1(data1)}/>
                </svg>
            {/if}
        {/each}
    </div>
    <div style="flex-grow: 1">
        <svg viewBox="0 0 200 50" class="line">
            <path class="path_part1 c2" d={pathLine_1(data1)}/>
        </svg>
    </div>
</div>


