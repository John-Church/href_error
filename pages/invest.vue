<template>
  <div class="w-full h-screen">
    <div class="w-full h-4/5 overflow-scroll">
      <div class="mx-auto h-full lg:flex items-center justify-center gap-2">
        <div class="">
          <img
            src="testingImage.png"
            alt="Look, Book, and Fly"
            class="lg:hidden block mx-auto"
          />
        </div>
        <div class="sm:max-w-lg px-4 pb-8 sm:px-16">
          <h1 class="text-4xl sm:text-7xl text-gray-800 font-semibold mb-4">
            <br class="hidden lg:block" />Test
          </h1>
          <a :href="testing_link">
            <button
              type="button"
              class="w-auto justify-center inline-flex items-center px-4 py-2 border border-transparent text-base font-medium rounded-sm shadow-sm text-white bg-green-400 hover:bg-green-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-400"
            >
              testing Now
            </button>
          </a>
        </div>
      </div>
    </div>
    <div to="/OC" class="w-full h-1/5">
      <NuxtLink
        target="_blank"
        to="/OC"
        class="p-4 sm:p-0 w-full h-16 absolute z-20 flex justify-center items-center text-xl md:text-3xl text-gray-700 bg-black bg-opacity-20"
      >
        Test Offering Circular
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6 ml-4"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"
          />
        </svg>
      </NuxtLink>
      <iframe
        class="w-full h-full"
        loading="lazy"
        src="/OC2"
        title="Test OC"
      ></iframe>
    </div>
  </div>
</template>

<script>
export default {
  layout: "none",
  data() {
    return {
      testing_link: "",
    };
  },
  mounted() {
    console.log(this.testing_link);

    let route_variables = {
      cmpid: this.$route.query.cmpid,
      sub1: this.$route.query.sub1,
      sub2: this.$route.query.sub2,
      sub3: this.$route.query.sub3,
      sub4: this.$route.query.sub4,
      sub5: this.$route.query.sub5,
      sub6: this.$route.query.sub6,
      sub7: this.$route.query.sub7,
      sub8: this.$route.query.sub8,
      utm_source: this.$route.query.utm_source,
      utm_medium: this.$route.query.utm_medium,
      utm_campaign: this.$route.query.utm_campaign,
    };

    if (route_variables["cmpid"] === undefined) {
      console.log(route_variables["cmpid"]);
      route_variables["cmpid"] = "6238ae576807c500011af384";
    }
    if (route_variables["utm_source"] === undefined) {
      route_variables["utm_source"] = "testoriginsite";
    }

    var newLink = "https://www.test.com/testorigin?";
    for (const property in route_variables) {
      if (route_variables[property] != undefined) {
        newLink += property + "=" + route_variables[property] + "&";
      }
    }
    this.testing_link = newLink;
    console.log(this.testing_link);
    console.log("=======");
  },
};
</script>

<style></style>
