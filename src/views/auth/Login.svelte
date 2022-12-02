<script>
  import { link } from "svelte-routing";

  // core components
  const github = "../assets/img/github.svg";
  const google = "../assets/img/google.svg";
  export let location;
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
            <small>로그인</small>
          </div>
          <form>
            <div class="relative w-full mb-3">
              <label
                class="block uppercase text-blueGray-600 text-xs font-bold mb-2"
                for="grid-email"
              >
                아이디
              </label>
              <input
                id="grid-email"
                type="text"
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


            <div class="text-center mt-6">
              <button
                class="bg-blueGray-800 text-white active:bg-blueGray-600 text-sm font-bold uppercase px-6 py-3 rounded shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 w-full ease-linear transition-all duration-150"
                type="button"
              >
                로그인
              </button>
            </div>
          </form>
        </div>
      </div>
      <div class="flex flex-wrap mt-6 relative">
<!--        <div class="w-1/2">-->
<!--          <a href="#pablo" on:click={(e) => e.preventDefault()} class="text-blueGray-200">-->
<!--            <small>비밀번호 찾기</small>-->
<!--          </a>-->
<!--        </div>-->
<!--        <div class="w-1/2 text-right">-->
<!--          <a use:link href="/auth/register" class="text-blueGray-200">-->
<!--            <small>유저 등록</small>-->
<!--          </a>-->
<!--        </div>-->
      </div>
    </div>
  </div>
</div>
