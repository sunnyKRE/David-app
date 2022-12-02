<script>
    import SheetForm from "./sheetForm.svelte";
    import Step from "../../moduels/Step.svelte"
    import Grid from "gridjs-svelte";
    import html from "gridjs-svelte";

    import data1 from './data'
    import data2 from './data2'
    import Graph from './Graph.svelte';
    import Approval_Line from './Approval_Line.svelte';
    import {afterUpdate, onMount} from "svelte";

    let dataTest = data1;

    let level_Top_Value = 0;
    let level_Down_Value = 0;
    let done_Value = 0;



    onMount(() => {


    })


    $: {


    }


    function both_done(){

        if(level_Top_Value >= 2 && level_Down_Value >= 4){
            if(done_Value === 0) {
                done_Value = 1
            }else if(done_Value === 1)
                done_Value = 2
        }
        else done_Value = 0;

    }



    function top_up(){
        if(level_Top_Value < 2){
            level_Top_Value++;
            both_done();
        }

    }
    function top_down(){
        if(level_Top_Value > 0){
            level_Top_Value--;
            both_done();
        }


    }
    function down_up(){
        if(level_Down_Value < 4){
            level_Down_Value++;
            both_done();
        }

    }
    function down_down(){
        if(level_Down_Value > 0){
            level_Down_Value--;
            both_done();
        }

    }
    function init(){
        level_Top_Value = 0;
        level_Down_Value = 0;
        both_done();
    }
    function done(){
        both_done()
    }

    const columns = [
        {'name':'dd'},
        {'name':'기룡전기'},
        {'name':'준공예정일 :'},
        {'name':'2022년 12월 31일'}]
    const data = [
        ['계약업체', '기룡전기', '준공예정일','2022년 12월 31일',''],
        ['계약금액','1,777,056,607','집행금액(직접비)','2,666,560','당초실행대비'],
        ['기성(준공)금액','1,777,056,607','집행율','0.15%','0.15%'],
        ['실행금액','1,771,110,618','실행금액\n(본사관리비포함)','147,606,985','공정율'],
        ['예정실행율','99.83%','실행율','8.32%','22%'],
    ]

    const className= {
        container: "table-wrapper"
    }

    const style =
        {
            table: {
                'font-size' : '12px',
                'text-align' : 'center',
                'white-space' : 'nowrap',
                'align-self' : 'center',
            },
            td:{
                'padding' : '8px 7px'

                // 'font-size' : '12px'
            },

            header:{
                'border' : '3px solid #ccc',

            }

        }


</script>


<hr class="mt-6 border-b-1 border-blueGray-300" />

<div class="text-blueGray-400 text-sm mt-3 mb-6 font-bold uppercase">
    결제
    <button type="button" on:click={() => {top_up()}} style="border-width: 2px; border-color: black;">
        top-up
    </button>
    <button type="button" on:click={() => {top_down()}} style="border-width: 2px; border-color: black;">
        top-down
    </button>
    <button type="button" on:click={() => {down_up()}} style="border-width: 2px; border-color: black;">
        down-up
    </button>
    <button type="button" on:click={() => {down_down()}} style="border-width: 2px; border-color: black;">
        down-down
    </button>
    <button type="button" on:click={() => {done()}} style="border-width: 2px; border-color: black;">
        done
    </button>
    <button type="button" on:click={() => {init()}} style="border-width: 2px; border-color: black;">
        init
    </button>
</div>


<div>
    <Approval_Line bind:level_TopSide={level_Top_Value} bind:level_DownSide={level_Down_Value}
                   steps_TopSide={['자산구매팀장','경영지원팀장']} steps_DownSide={['담당','팀장','총괄','이사']} steps_Last={'대표이사'} done={done_Value} />
</div>



<hr class="mt-6 border-b-1 border-blueGray-300" />

<h6 class="text-blueGray-400 text-sm mt-3 mb-6 font-bold uppercase">
    프로젝트 정보
</h6>
<div style=" overflow: auto;">
    <div  style="font-size:12px; margin: 0 auto; width: fit-content;">
        <Grid {data} {className} {style}/>

    </div>
</div>


<hr class="mt-6 border-b-1 border-blueGray-300" />


<div class="text-blueGray-400 text-sm mt-3 mb-6 font-bold uppercase" style="display: flex; justify-content: space-between;">
    조회 내역
    <div style="text-align: right;"></div>
    <button  class="align-middle text-center bg-indigo-500 text-white active:bg-indigo-600  font-bold uppercase px-3 py-1 rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
             type="button" >추가</button>


</div >

<SheetForm />


<!--544.13-->


