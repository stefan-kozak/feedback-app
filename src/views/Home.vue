<template>
  <div class="wrap flex flex-col lg:flex-row justify-center w-full">
    <aside
      class="side-bar px-5 lg:px-0 flex flex-row lg:flex-col w-full lg:w-1/6"
    >
      <header
        class="
          rounded-2xl
          bg-gradient-to-r
          from-purple-400
          via-pink-500
          to-red-500
          p-10
          text-white
          lg:mr-0
          mr-5
        "
      >
        <h1 class="text-2xl font-bold">Frontend Mentor</h1>
        <p class="text-md text-gray-200">Feedback Board</p>
      </header>

      <div
        class="
          flex flex-row flex-wrap
          side-bar-tag-filter
          lg:mt-5 lg:mr-0
          mt-0
          mr-3
          p-5
          rounded-2xl
          bg-white
        "
      >
        <SearchTag :isActiveProp="true" @toggle-tag-filter="toggleSearchTag">
          All
        </SearchTag>
        <SearchTag @toggle-tag-filter="toggleSearchTag"> UI </SearchTag>
        <SearchTag @toggle-tag-filter="toggleSearchTag"> UX </SearchTag>
        <SearchTag @toggle-tag-filter="toggleSearchTag">
          Enhancement
        </SearchTag>
        <SearchTag @toggle-tag-filter="toggleSearchTag"> Bug </SearchTag>
        <SearchTag @toggle-tag-filter="toggleSearchTag"> Feature </SearchTag>
      </div>

      <div
        class="
          side-bar-dashboard
          flex flex-col
          p-5
          side-bar-tag-filter
          lg:mt-5
          rounded-2xl
          bg-white
        "
      >
        <div class="flex flex-row justify-between items-center pb-3">
          <h1 class="font-bold text-2xl text-indigo-900">Roadmap</h1>
          <a href="" class="underline text-blue-900 font-bold text-xl">View</a>
        </div>
        <ul>
          <li class="flex flex-row">
            <svg
              viewBox="0 0 32 32"
              class="fill-current w-2 mr-2 text-red-300"
              xmlns="http://www.w3.org/2000/svg"
            >
              <circle cx="16" cy="16" r="16" />
            </svg>
            <p>Planned</p>
          </li>
          <li class="flex flex-row">
            <svg
              viewBox="0 0 32 32"
              class="fill-current w-2 mr-2 text-purple-800"
              xmlns="http://www.w3.org/2000/svg"
            >
              <circle cx="16" cy="16" r="16" />
            </svg>
            <p>In Progress</p>
          </li>
          <li class="flex flex-row">
            <svg
              viewBox="0 0 32 32"
              class="fill-current w-2 mr-2 text-blue-400"
              xmlns="http://www.w3.org/2000/svg"
            >
              <circle cx="16" cy="16" r="16" />
            </svg>
            <p>Live</p>
          </li>
        </ul>
      </div>
    </aside>

    <main class="lg:w-2/4 w-full px-5 mt-5 lg:mt-0">
      <header
        class="
          bg-indigo-900
          text-white
          p-5
          w-full
          rounded-2xl
          flex flex-row
          justify-between
          items-center
        "
      >
        <div class="info flex flex-row">
          <div class="flex flex-row">
            <img
              class="ml-3 mr-5"
              src="@/assets/suggestions/icon-suggestions.svg"
              alt="icon-suggestions"
            />
            <h1 class="font-bold">0 Suggestions</h1>
          </div>

          <div class="flex flex-row items-center ml-5">
            <h5>Sort by:</h5>
            <p class="ml-1 font-bold">Most updates</p>
            <svg
              class="ml-2"
              width="10"
              height="7"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path d="M1 1l4 4 4-4" stroke="#fff" stroke-width="2" />
            </svg>
          </div>
        </div>

        <div
          class="
            component-add
            self-end
            mr-3
            px-8
            py-3
            lg:py-3
            rounded-xl
            bg-purple-700
            cursor-pointer
          "
        >
          <h1 class="font-bold">+ Add Feedback</h1>
        </div>
      </header>
      <section
        v-cloak
        class="
          flex flex-col
          items-center
          mt-5
          p-5
          pb-20
          bg-white
          w-full
          rounded-xl
        "
      >
        <img
          class="w-2/12 self-center mt-10"
          src="@/assets/suggestions/illustration-empty.svg"
          alt="without feedback"
        />
        <h1 class="w-max mt-10 font-bold text-3xl">There is no feedback yet</h1>
        <p class="w-3/6 text-center mt-5 mb-10">
          Got a suggestion? Found a bug that needs to be squashed? We love
          hearing about new ideas to improve our app.
        </p>
      </section>
    </main>
  </div>
</template>

<script>
import SearchTag from "@/components/SearchTag.vue";

export default {
  name: "Home",
  components: {
    SearchTag,
  },

  data() {
    return {
      searchFilterTags: ["All"],
    };
  },

  methods: {
    toggleSearchTag(tagName) {
      if (this.searchFilterTags.includes(tagName)) {
        this.searchFilterTags = this.searchFilterTags.filter(
          (tag) => tag != tagName
        );
        return;
      } else {
        this.searchFilterTags.push(tagName);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
[v-cloak] {
  display: none;
}
</style>
