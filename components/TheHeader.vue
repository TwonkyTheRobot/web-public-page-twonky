<template>
  <div class="w-full relative bg-white border-b-2 border-black">
    <header class="px-4 sm:px-6 flex tracking-wide font-display">
      <nav class="py-3 sm:py-5 flex w-full items-center">
        <NuxtLink
          class="text-lime-400 transition-colors duration-700 text-xl font-black uppercase text-shadow-sharp hover:text-brown"
          to="/"
        >
          <span>Hej hej!</span>
        </NuxtLink>

        <div class="flex-grow"></div>
      
        <div class="">
          <Popover v-slot="{ open }" class="">
            <PopoverButton
              class="group inline-flex items-center rounded-md text-black px-3 py-2 text-base font-medium transition-colors text-white hover:bg-gray-300"
            >
              <span class="mr-2 hidden sm:inline" >Meny</span>
              <XIcon v-if="open" class="h-5 w-5 text-gray-400" aria-hidden="true" />
              <MenuIcon  v-else class="h-5 w-5 text-gray-400" aria-hidden="true" />
            </PopoverButton>

            <transition
              enter-active-class="transition duration-200 ease-out"
              enter-from-class="translate-y-1 opacity-0"
              enter-to-class="translate-y-0 opacity-100"
              leave-active-class="transition duration-150 ease-in"
              leave-from-class="translate-y-0 opacity-100"
              leave-to-class="translate-y-1 opacity-0"
            >
              <PopoverPanel
                class="absolute shadow-sharp right-0 bg-lime-100 z-10 mt-3 w-screen max-w-sm  px-4 sm:px-0"
              >
                <ul class="flex flex-col">
                  <li>
                    <NuxtLink
                      class="text-black p-4 block font-semibold hover:underline"
                      to="/kundservice/vanliga-fragor"
                      >Vanliga frågor</NuxtLink
                    >
                  </li>
                  <li>
                    <NuxtLink
                      class="text-black p-4 block font-semibold hover:underline"
                      to="/kundservice"
                      >Kundservice</NuxtLink
                    >
                  </li>
                </ul>
              </PopoverPanel>
            </transition>
          </Popover>
        </div>
      </nav>
      
     
    </header>
  </div>
</template>

<script setup lang="ts">
import { Popover, PopoverButton, PopoverPanel } from "@headlessui/vue";
import { MenuIcon, XIcon } from "@heroicons/vue/solid";

const solutions = [
  {
    name: "Insights",
    description: "Measure actions your users take",
    href: "##",
    icon: `
      <svg
        width="48"
        height="48"
        viewBox="0 0 48 48"
        fill="none"
        aria-hidden="true"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect width="48" height="48" rx="8" fill="#FFEDD5" />
        <path
          d="M24 11L35.2583 17.5V30.5L24 37L12.7417 30.5V17.5L24 11Z"
          stroke="#FB923C"
          stroke-width="2"
        />
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M16.7417 19.8094V28.1906L24 32.3812L31.2584 28.1906V19.8094L24 15.6188L16.7417 19.8094Z"
          stroke="#FDBA74"
          stroke-width="2"
        />
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M20.7417 22.1196V25.882L24 27.7632L27.2584 25.882V22.1196L24 20.2384L20.7417 22.1196Z"
          stroke="#FDBA74"
          stroke-width="2"
        />
      </svg>
    `,
  },
  {
    name: "Automations",
    description: "Create your own targeted content",
    href: "##",
    icon: `
      <svg
        width="48"
        height="48"
        viewBox="0 0 48 48"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect width="48" height="48" rx="8" fill="#FFEDD5" />
        <path
          d="M28.0413 20L23.9998 13L19.9585 20M32.0828 27.0001L36.1242 34H28.0415M19.9585 34H11.8755L15.9171 27"
          stroke="#FB923C"
          stroke-width="2"
        />
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M18.804 30H29.1963L24.0001 21L18.804 30Z"
          stroke="#FDBA74"
          stroke-width="2"
        />
      </svg>
    `,
  },
  {
    name: "Reports",
    description: "Keep track of your growth",
    href: "##",
    icon: `
      <svg
        width="48"
        height="48"
        viewBox="0 0 48 48"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect width="48" height="48" rx="8" fill="#FFEDD5" />
        <rect x="13" y="32" width="2" height="4" fill="#FDBA74" />
        <rect x="17" y="28" width="2" height="8" fill="#FDBA74" />
        <rect x="21" y="24" width="2" height="12" fill="#FDBA74" />
        <rect x="25" y="20" width="2" height="16" fill="#FDBA74" />
        <rect x="29" y="16" width="2" height="20" fill="#FB923C" />
        <rect x="33" y="12" width="2" height="24" fill="#FB923C" />
      </svg>
    `,
  },
];
</script>
