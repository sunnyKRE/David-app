<script>

    $: innerWidth = 0
    import {onMount} from 'svelte';
    import { draw, fade } from 'svelte/transition';

    import { extent } from 'd3-array';
    import { scaleLinear } from 'd3-scale';
    import { line, curveBasis } from 'd3-shape';
    import data_fall from "./data2"
    import data_line from "./data"
    import data_rise from "./data3"


    // the props
    let index;
    export let steps_TopSide;
    export let steps_DownSide;
    export let steps_Last;
    export let level_TopSide;
    export let level_DownSide;
    export let done;

    let xScale_Line;
    let yScale_Line;
    let pathLine_Line;
    let xScale_TopSide;
    let yScale_TopSide;
    let pathLine_TopSide;
    let xScale_DownSide;
    let yScale_DownSide;
    let pathLine_DownSide;

    let circle_Outer = innerWidth / 960;
    let circle_Inner = circle_Outer * 1.25 / 2;

    let circles_Outer;


// 960 : 1 : 1.25/2

    onMount(() => {
        circles_Outer = document.querySelectorAll("#circle_Outer")
        circle_Inner = circle_Outer * 1.25 / 2;
    })
    $: {

        console.log(circles_Outer)


        xScale_TopSide = scaleLinear()
            .domain(extent(data_fall.map(d => d.valueX)))
            .range([0, innerWidth/6.8]);

        pathLine_TopSide = line()
            .x(d => xScale_TopSide(d.valueX))
            .y(d => yScale_TopSide(d.valueY))
            .curve(curveBasis)

        xScale_DownSide = scaleLinear()
            .domain(extent(data_rise.map(d => d.valueX)))
            .range([0, innerWidth/6.8]);

        pathLine_DownSide = line()
            .x(d => xScale_DownSide(d.valueX))
            .y(d => yScale_DownSide(d.valueY))
            .curve(curveBasis)

    }
    // the scales


    xScale_Line = scaleLinear()
        .domain(extent(data_line.map(d => d.valueX)))
        .range([0, 2000]);

    yScale_Line = scaleLinear()
        .domain(extent(data_line.map(d => d.valueY)))
        .range([25, 25]);

    pathLine_Line = line()
        .x(d => xScale_Line(d.valueX))
        .y(d => yScale_Line(d.valueY))
        .curve(curveBasis)



    xScale_TopSide = scaleLinear()
        .domain(extent(data_fall.map(d => d.valueX)))
        .range([0, 376]);

    yScale_TopSide = scaleLinear()
        .domain(extent(data_fall.map(d => d.valueY)))
        .range([125, 150]);

    pathLine_TopSide = line()
        .x(d => xScale_TopSide(d.valueX))
        .y(d => yScale_TopSide(d.valueY))
        .curve(curveBasis)



    xScale_DownSide = scaleLinear()
        .domain(extent(data_rise.map(d => d.valueX)))
        .range([0, 376]);

    yScale_DownSide = scaleLinear()
        .domain(extent(data_rise.map(d => d.valueY)))
        .range([0, 25]);

    pathLine_DownSide = line()
        .x(d => xScale_DownSide(d.valueX))
        .y(d => yScale_DownSide(d.valueY))
        .curve(curveBasis)


</script>

<svelte:window bind:innerWidth />
<div style="height: 10px"> </div>
<div style="display: flex; justify-content: space-between; margin:0 10%; height: 50px; align-items: center">
    <div style="display: flex; flex-direction: column; width: 76%;">
        <div style="display: flex; justify-content: space-between; height: 50px">
            {#each steps_TopSide as step_1, index }
                <div class="step__cover">
                    <label class="step__text top">{step_1}</label>

                    {#if level_TopSide <= index}
                        {#if level_TopSide === index}
                            <div class="step__cover__circle">
                                <div class="step__cover__circle waiting"></div>
                            </div>
                        {:else}
                            <div class="step__cover__circle"></div>
                        {/if}
                    {:else}
                        <div class="step__cover__circle done"></div>
                    {/if}
                </div>
                <svg viewBox="0 0 auto auto" class="line" style="width: 100%">
                    {#if level_TopSide <= index}
                        <path d={pathLine_Line(data_line)} class="confirmLine"/>
                    {:else}
                        <path d={pathLine_Line(data_line)} class="confirmLine active"/>
                    {/if}
                </svg>

            {/each}
        </div>
        <div style="display: flex;  height: 50px;">
            {#each steps_DownSide as step_2, index }
                <div class="step__cover">
                    <label class="step__text bottom ">{step_2}</label>
                    {#if level_DownSide <= index}
                        {#if level_DownSide === index}
                            <div class="step__cover__circle">
                                <div class="step__cover__circle waiting"></div>
                            </div>
                        {:else}
                            <div class="step__cover__circle"></div>
                        {/if}
                    {:else}
                        <div class="step__cover__circle done"></div>
                    {/if}
                </div>
                <svg viewBox="0 0 auto auto" class="line" style="width: 100%">
                    {#if level_DownSide <= index}
                        <path d={pathLine_Line(data_line)} class="confirmLine"/>
                    {:else}
                        <path d={pathLine_Line(data_line)} class="confirmLine active"/>
                    {/if}
                </svg>
            {/each}
        </div>
    </div>
    <div style="display: flex; justify-content: space-between; flex-direction: column; width: 24%">
        {#if done === 0}
            <svg viewBox="auto">
                <path d={pathLine_TopSide(data_fall)} class="confirmLine"/>
            </svg>
            <svg viewBox="0 0 auto auto">
                <path d={pathLine_DownSide(data_rise)} class="confirmLine"/>
            </svg>
        {:else}
            <svg viewBox="0 0 auto auto">
                <path d={pathLine_TopSide(data_fall)} class="confirmLine active"/>
            </svg>
            <svg viewBox="0 0 auto auto">
                <path d={pathLine_DownSide(data_rise)} class="confirmLine active"/>
            </svg>
        {/if}



    </div>
    <div style="transform: translate(-100%);">
        <label class="step__text last">{steps_Last}</label>

        {#if done === 0}
            <div class="step__cover__circle"></div>
        {:else if done === 1}
            <div class="step__cover__circle">
                <div class="step__cover__circle waiting"></div>
            </div>
        {:else}
            <div class="step__cover__circle done"></div>
        {/if}
    </div>



</div>
<div  id="circle_Outer"  style="height: 30px"> </div>



