
    import {scaleLinear} from "d3-scale";
    import {extent} from "d3-array";
    import {curveBasis, line} from "d3-shape";
    import data1 from "./data";
    import data2 from "./data2";

    export let xScale;
    export let yScale;
    export let pathLine;
    export let lineTest;
    let data;
    data = data1

    xScale = scaleLinear()
        .domain(extent(data.map(d => d.valueX)))
        .range([0, 150]);

    yScale = scaleLinear()
        .domain(extent(data.map(d => d.valueY)))
        .range([0, 50]);

    // the path generator
    pathLine = line()
        .x(d => xScale(d.valueX))
        .y(d => yScale(d.valueY))
        .curve(curveBasis)

    lineTest = line()
        .x(d => xScale(d.valueX))
        .y(d => yScale(d.valueY))
