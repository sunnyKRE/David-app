<script>
  import Step from "../../moduels/Step.svelte"

  import Approval_Line_2 from "./Approval_Line_2.svelte";

  let level_TopSide;
  let level_DownSide
  $: innerHeight = 0
  let maxHeight;

  $: {

    maxHeight = innerHeight * 0.8;
  }

</script>


<svelte:window bind:innerHeight />
<div
  class="relative flex flex-col min-w-0 break-words bg-white w-full mb-6 shadow-lg rounded"
  style="max-height: {maxHeight}px;"
>

  <div class="rounded-t mb-0 px-4 py-3 border-0">
    <div class="flex flex-wrap items-center">
      <div class="relative w-full px-4 max-w-full flex-grow flex-1">
        <h3 class="font-semibold text-base text-blueGray-700">
          결제 현황
        </h3>
      </div>
<!--      <div class="relative w-full px-4 max-w-full flex-grow flex-1 text-right">-->
<!--        <button-->
<!--          class="bg-indigo-500 text-white active:bg-indigo-600 text-xs font-bold uppercase px-3 py-1 rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"-->
<!--          type="button"-->
<!--        >-->
<!--          준공 완료까지 표시-->
<!--        </button>-->
<!--      </div>-->
    </div>
  </div>
  <div class="block w-full overflow-x-auto">
    <!-- Projects table -->
    <table class="items-center w-full bg-transparent border-collapse">
      <thead class="thead-light">
      <tr>
        <th
                class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
        >
          직영 / 외주
        </th>
        <th
                class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
        >
          팀
        </th>
        <th
                class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
        >
          프로젝트
        </th>
        <th
                class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
        >
          구분
        </th>
        <th
                class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
        >
          진행도

        </th>
        <th
                class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
        >
        </th>
      </tr>
      </thead>
      <tbody >
      {#each Array(11) as _}

      <tr>
        <th
                class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4 text-left"
        >
          외주

        </th>
        <td
                class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
        >
          팀1
        </td>
        <td
                class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
        >
          프로젝트1

        </td>
        <td
                class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4 "
        >
          10월 / 1





        </td>
        <td
                class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4" style="align-items: center; width: 30%"
        >


            <Approval_Line_2 level_TopSide={1} level_DownSide={2}  steps_TopSide={['','']} steps_DownSide={['','','','']} steps_Last="{''}" done={0} status={0}/>





        </td>
        <td class="text-center">
          <button  class="align-middle text-center bg-indigo-500 text-white active:bg-indigo-600  font-bold uppercase px-3 py-1 rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
                   type="button" on:click{}>결제</button>

        </td>

      </tr>


        {/each}






















        </tbody>
    </table>
  </div>
</div>
