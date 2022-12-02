<script>
  // core components
  const github = "../assets/img/github.svg";
  const google = "../assets/img/google.svg";
  export let location;
  // import { Dropdown } from "carbon-components-svelte";
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

  let selected;

  let answer = '';
</script>

<div class="container mx-auto px-4 h-full">
  <div class="flex content-center items-center justify-center h-full">
    <div class="w-full lg:w-4/12 px-4">
      <div
        class="relative flex flex-col min-w-0 break-words w-full mb-6 shadow-lg rounded-lg bg-blueGray-200 border-0"
      >
        <div class="rounded-t mb-0 px-6 py-2">


        </div>
        <div class="flex-auto px-4 lg:px-10 py-10 pt-0">
          <div class="text-blueGray-400 text-center mb-3 font-bold">
            <small>유저 등록</small>
          </div>
          <form>
            <div class="relative w-full mb-3">
              <label
                class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
                for="grid-name"
              >
                아이디
              </label>
              <input
                id="grid-name"
                type="email"
                class="border-0 px-3 py-3 placeholder-blueGray-300 text-blueGray-600 bg-white rounded text-sm shadow focus:outline-none focus:ring w-full ease-linear transition-all duration-150"
                placeholder="아이디"
              />
            </div>
            <div class="relative w-full mb-3">
              <label
                      class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
                      for="grid-password"
              >
                비밀번호
              </label>
              <input
                      id="grid-password"
                      type="password"
                      class="border-0 px-3 py-3 placeholder-blueGray-300 text-blueGray-600 bg-white rounded text-sm shadow focus:outline-none focus:ring w-full ease-linear transition-all duration-150"
                      placeholder="비밀번호"
              />
            </div>
            <div class="relative w-full mb-3">
              <label
                      class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
              >
                구분
              </label>
              <select class="relative w-full mb-3" value={selected} on:change="{() => answer = ''}">
                {#each questions as question}
                  <option value={question}>
                    {question.text}
                  </option>
                {/each}
              </select>

            </div>



            <div class="text-center mt-6">
              <button
                class="bg-blueGray-800 text-white active:bg-blueGray-600 text-sm font-bold uppercase px-6 py-3 rounded shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 w-full ease-linear transition-all duration-150"
                type="button"
              >
                유저 등록
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</div>
