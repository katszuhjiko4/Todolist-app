<template>
  <div>
    <!-- For NavBar -->
    <nav
      class="border-gray-200 bg-gray-50 dark:bg-gray-800 dark:border-gray-700"
    >
      <div
        class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4"
      >
        <a href="#" class="flex items-center">
          <img src="@/assets/tdl.png" class="h-8 mr-3" alt="tdl Logo" />
          <span
            class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white"
          >
            Myproject1</span
          >
        </a>
        <button
          data-collapse-toggle="navbar-solid-bg"
          type="button"
          class="inline-flex items-center p-2 ml-3 text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
          aria-controls="navbar-solid-bg"
          aria-expanded="false"
        >
          <span class="sr-only">Open main menu</span>
          <svg
            class="w-6 h-6"
            aria-hidden="true"
            fill="currentColor"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
              clip-rule="evenodd"
            ></path>
          </svg>
        </button>
        <div class="hidden w-full md:block md:w-auto" id="navbar-solid-bg">
          <ul
            class="flex flex-col font-medium mt-4 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:border-0 md:bg-transparent dark:bg-gray-800 md:dark:bg-transparent dark:border-gray-700"
          >
            <li>
              <a
                href="#"
                class="block py-2 pl-3 pr-4 text-white bg-blue-700 rounded md:bg-transparent md:text-blue-700 md:p-0 md:dark:text-blue-500 dark:bg-blue-600 md:dark:bg-transparent"
                aria-current="page"
                >Todo List</a
              >
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <!-- For TodoLists Cont -->
    <div class="place-content-center mx-auto pl-56">
      <div class="bg-gray-200 w-4/5">
        <div class="border-2 border-gray-300 pt-8 pl-6 h-full">
          <h1 class="font-bold font-sans text-2xl pb-7">TodoList</h1>
        </div>
        <div class="text-center pt-2">
          <div class="flex place-content-center">
            <!-- Form for ID -->
            <form @submit.prevent="AddItems1" class="flex items-center mb-4">
              <input
                type="text"
                v-model="input1"
                class="rounded-l px-3 py-2 w-full"
              />
              <!-- Form for Des -->
              <form @submit.prevent="AddItems1" class="flex items-center mb-4">
                <input
                  type="text"
                  v-model="input2"
                  class="rounded-l px-3 py-2 w-full"
                />
                <!-- Form for Sta -->
                <form
                  @submit.prevent="AddItems1"
                  class="flex items-center mb-4"
                >
                  <input
                    type="text"
                    v-model="input3"
                    class="rounded-l px-3 py-2 w-full"
                  />
                  <button
                    type="submit"
                    class="bg-green-500 hover:bg-green-600 text-white font-bold rounded-r px-3 py-2 mr-2"
                  >
                    Add
                  </button>
                </form>
              </form>
            </form>
          </div>
        </div>
        <!-- For table Title -->
        <div class="container text-center mt-5 mb-5">
          <h1 class="mt-5 fw-bolder text-success italic font-bold">
            My Todo Lists Table
          </h1>
        </div>
        <!-- For table Container -->
        <div class="flex h-auto pb-2 pt-2 place-content-center pl-6">
          <div class="border-2 w-96 border-gray-700">
            <div class="flex">
              <span class="mx-6">ID</span>
              <span class="mx-6">Description</span>
              <span class="mx-6">Status</span>
            </div>
            <div class="flex justify-start mr-4">
              <ul>
                <!-- For ID -->
                <li
                  v-for="(todo, index) in todos"
                  :key="index"
                  class="flex items-center py-2 border-gray-800"
                >
                  <span class="mr-4">{{ todo }}</span>
                </li>
                <!-- For Description -->
                <li
                  v-for="(todo, index) in todos2"
                  :key="index"
                  class="flex items-center py-2 border-gray-800"
                >
                  <span class="mr-4">{{ todo }}</span>
                </li>
                <!-- For Status -->
                <li
                  v-for="(todo, index) in todos3"
                  :key="index"
                  class="flex items-center py-2 border-gray-800"
                >
                  <span class="mr-4">{{ todo }}</span>
                </li>
              </ul>
            </div>
          </div>
          <!-- For table Settings Delete and Update -->
          <button
            data-modal-target="popup-modal"
            data-modal-toggle="popup-modal"
            class="block text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
            type="button"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-6 h-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0"
              />
            </svg>
          </button>
          <div
            id="popup-modal"
            tabindex="-1"
            class="fixed top-0 left-0 right-0 z-50 hidden p-4 overflow-x-hidden overflow-y-auto md:inset-0 h-[calc(100%-1rem)] max-h-full"
          >
            <div class="relative w-full max-w-md max-h-full">
              <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
                <button
                  type="button"
                  class="absolute top-3 right-2.5 text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-800 dark:hover:text-white"
                  data-modal-hide="popup-modal"
                >
                  <svg
                    aria-hidden="true"
                    class="w-5 h-5"
                    fill="currentColor"
                    viewBox="0 0 20 20"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      fill-rule="evenodd"
                      d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                      clip-rule="evenodd"
                    ></path>
                  </svg>
                  <span class="sr-only">Close modal</span>
                </button>
                <div class="p-6 text-center">
                  <svg
                    aria-hidden="true"
                    class="mx-auto mb-4 text-gray-400 w-14 h-14 dark:text-gray-200"
                    fill="none"
                    stroke="currentColor"
                    viewBox="0 0 24 24"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
                    ></path>
                  </svg>
                  <h3
                    class="mb-5 text-lg font-normal text-gray-500 dark:text-gray-400"
                  >
                    Are you sure you want to delete this item?
                  </h3>
                  <button
                    @click="removeItems(index)"
                    data-modal-hide="popup-modal"
                    type="button"
                    class="text-white bg-red-600 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-red-300 dark:focus:ring-red-800 font-medium rounded-lg text-sm inline-flex items-center px-5 py-2.5 text-center mr-2"
                  >
                    Yes, I'm sure
                  </button>
                  <button
                    data-modal-hide="popup-modal"
                    type="button"
                    class="text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-gray-200 rounded-lg border border-gray-200 text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10 dark:bg-gray-700 dark:text-gray-300 dark:border-gray-500 dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-gray-600"
                  >
                    No, cancel
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
 

<script>
export default {
  data() {
    return {
      input1: "",
      input2: "",
      input3: "",
      todos: [],
      todos2: [],
      todos3: [],
    };
  },
  methods: {
    AddItems1() {
      if ((this.input1, this.input2, this.input3 !== "")) {
        this.todos.push(this.input1);
        this.todos2.push(this.input2);
        this.todos3.push(this.input3);
        this.input1 = "";
        this.input2 = "";
        this.input3 = "";
      }
    },
    removeItems(index) {
      console.log("");
      this.todos.splice(index, 1);
      this.todos2.splice(index, 1);
      this.todos3.splice(index, 1);
    },
  },
};
</script>