<script>

  import LookupResult from "./LookupResult.svelte";
  import SheetForm from "./sheetForm.svelte"
  import data from './data.js';
  import data2 from './data2.js';
  import Graph from './Graph.svelte';
  import Lookup from "../../views/admin/Lookup.svelte";

  const index = 0;
  let dataTest = null;
  if(index === 4){
    dataTest = data;
  }else{
    dataTest = data2
  }


  let show = false;




  let division = [
    { id: 1, text: `직영` },
    { id: 2, text: `외주` },

  ];




  let questions = [
    { id: 1, text: `관리자1` },
    { id: 2, text: `관리자2` },
    { id: 3, text: `관리자3` },
    { id: 4, text: `관리자4` },
    { id: 5, text: `관리자5` },
    { id: 6, text: `관리자6` },
    { id: 7, text: `관리자7` },
    { id: 8, text: `일반사용자` }
  ];

  let projects = [
    { id: 1, text: `프로젝트1` },
    { id: 2, text: `프로젝트2` },
    { id: 3, text: `프로젝트3` },
    { id: 4, text: `프로젝트4` },
    { id: 5, text: `프로젝트5` },
    { id: 6, text: `프로젝트6` },
    { id: 7, text: `프로젝트7` },
    { id: 7, text: `프로젝트7` },
    { id: 1, text: `프로젝트1` },
    { id: 2, text: `프로젝트2` },
    { id: 3, text: `프로젝트3` },
    { id: 4, text: `프로젝트4` },
    { id: 5, text: `프로젝트5` },
    { id: 6, text: `프로젝트6` },
    { id: 7, text: `프로젝트7` },
    { id: 7, text: `프로젝트7` },
    { id: 1, text: `프로젝트1` },
    { id: 2, text: `프로젝트2` },
    { id: 3, text: `프로젝트3` },
    { id: 4, text: `프로젝트4` },
    { id: 5, text: `프로젝트5` },
    { id: 6, text: `프로젝트6` },
    { id: 7, text: `프로젝트7` },
    { id: 7, text: `프로젝트7` },
    { id: 1, text: `프로젝트1` },
    { id: 2, text: `프로젝트2` },
    { id: 3, text: `프로젝트3` },
    { id: 4, text: `프로젝트4` },
    { id: 5, text: `프로젝트5` },
    { id: 6, text: `프로젝트6` },
    { id: 7, text: `프로젝트7` },
    { id: 7, text: `프로젝트7` },
    { id: 1, text: `프로젝트1` },
    { id: 2, text: `프로젝트2` },
    { id: 3, text: `프로젝트3` },
    { id: 4, text: `프로젝트4` },
    { id: 5, text: `프로젝트5` },
    { id: 6, text: `프로젝트6` },
    { id: 7, text: `프로젝트7` },
    { id: 7, text: `프로젝트7` },
    { id: 1, text: `프로젝트1` },
    { id: 2, text: `프로젝트2` },
    { id: 3, text: `프로젝트3` },
    { id: 4, text: `프로젝트4` },
    { id: 5, text: `프로젝트5` },
    { id: 6, text: `프로젝트6` },
    { id: 7, text: `프로젝트7` },
    { id: 7, text: `프로젝트7` },

    { id: 8, text: `프로젝트8` }
  ];

  let years = [
    { id: 1, text: `2022` },
    { id: 2, text: `2023` },
    { id: 3, text: `2024` },
    { id: 4, text: `2025` },

  ];

  let months = [
    { id: 1, text: `11` },
    { id: 2, text: `12` },
    { id: 3, text: `1` },
    { id: 4, text: `2` },

  ];
  let selected;

  let answer = '';

  let testWidth;
  let testHeight;

  let level = 0;

  function levelControl(){
    if(level > 4) level=0;
    else level ++;
    console.log(level);
  }

  $: dd = testWidth^2 + testHeight^2





</script>


<div
  class="relative flex flex-col min-w-0 break-words w-full mb-6 shadow-lg rounded-lg bg-blueGray-100 border-0"
>
  <div class="rounded-t bg-white mb-0 px-6 py-6">
    <div class="text-center flex justify-between">
      <h6 class="text-blueGray-700 text-xl font-bold">정산서 조회</h6>
<!--      <button-->
<!--        class="bg-red-400 text-white active:bg-red-500 font-bold uppercase text-xs px-4 py-2 rounded shadow hover:shadow-md outline-none focus:outline-none mr-1 ease-linear transition-all duration-150"-->
<!--        type="button"-->
<!--      >-->
<!--        Settings-->
<!--      </button>-->
    </div>
  </div>
  <div class="flex-auto px-4 lg:px-10 py-10 pt-0" style="padding-bottom: 1rem">
    <form >
      <h6 class="text-blueGray-400 text-sm mt-3 mb-6 font-bold uppercase">
        조회 조건
      </h6>
      <div class="flex flex-wrap" >
        <div class="w-full lg:w-4/12 px-4">
          <div class="relative w-full mb-3">
            <label
                    class="block uppercase text-blueGray-600 text-xs font-bold mb-2"

            >
              구분
            </label>
            <select class=" text-sm relative w-full mb-3 h-10" value={selected} on:change="{() => answer = ''}">
              id="grid-username"
              {#each division as question}
                <option value={question}>
                  {question.text}
                </option>
              {/each}
            </select>
          </div>
        </div>
        <div class="w-full lg:w-4/12 px-4">
          <div class="relative w-full mb-3">
            <label
              class="block uppercase text-blueGray-600 text-xs font-bold mb-2"

            >
              팀
            </label>
            <select class="text-sm relative w-full mb-3 h-10" value={selected} on:change="{() => answer = ''}">
              id="grid-username"
              {#each questions as question}
                <option value={question}>
                  {question.text}
                </option>
              {/each}
            </select>
          </div>
        </div>
        <div class="w-full lg:w-4/12 px-4">
          <div class="relative w-full mb-3">
            <label
              class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
            >
              프로젝트
            </label>
            <select class="text-sm relative w-full mb-3 h-10" value={selected} on:change="{() => answer = ''}">
              {#each projects as project}
                <option value={project}>
                  {project.text}
                </option>
              {/each}
            </select>
          </div>
        </div>

        <div class="w-full lg:w-2c5/12 px-4">
          <div class="relative w-full mb-3">
            <label
                    class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
            >
              연도
            </label>
            <select class="text-sm relative w-full mb-3 h-10" value={selected} on:change="{() => answer = ''}">
              {#each years as year}
                <option value={year}>
                  {year.text}
                </option>
              {/each}
            </select>
          </div>
        </div>
        <div class="w-full lg:w-2c5/12 px-4">
          <div class="relative w-full mb-3">
            <label
                    class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
            >
              월
            </label>
            <select class="text-sm relative w-full mb-3 h-10" value={selected} on:change="{() => answer = ''}">
              {#each months as month}
                <option value={month}>
                  {month.text}
                </option>
              {/each}
            </select>
          </div>
        </div>
        <div class="-align-center">

        </div>
        <div class="w-full lg:w-2c5/12 px-4">
          <div class="relative w-full mb-3">
            <label
                    class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
            >
              연도
            </label>
            <select class="text-sm relative w-full mb-3 h-10" value={selected} on:change="{() => answer = ''}">
              {#each years as year}
                <option value={year}>
                  {year.text}
                </option>
              {/each}
            </select>
          </div>
        </div>
        <div class="w-full lg:w-2c5/12 px-4">
          <div class="relative w-full mb-3">
            <label
                    class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
            >
              월
            </label>
            <select class="text-sm relative w-full mb-3 h-10" value={selected} on:change="{() => answer = ''}">
              {#each months as month}
                <option value={month}>
                  {month.text}
                </option>
              {/each}
            </select>
          </div>
        </div>

        <div class="w-full lg:w-2c5/12 px-4">
          <div class="relative w-full mb-3" style="height: 40%">
            <label
                    class="text-center align-middle block uppercase text-blueGray-600 text-xs font-bold mb-2"
            >
              &nbsp
            </label>
            <button  class="w-full h-full bg-indigo-500 text-white active:bg-indigo-600  font-bold uppercase align-bottom rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
                     type="button" on:click{}>조회</button>
          </div>

        </div>
      </div>

      <LookupResult />

    </form>

  </div>





</div>






