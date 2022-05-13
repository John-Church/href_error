<template>
  <div>
    <h2>Explanation</h2>
    <p>
      The link below to google.com should append the url variable 'test' to the
      end of the link.
    </p>
    <p>
      For example: "localhost:3000?test=1234" should result in the link
      "google.com?test=1234"
    </p>
    <p>This functionality works locally but does not work in production.</p>
    <h2>Links</h2>
    <a :href="generated_link">
      <button type="button">Press Me</button>
    </a>
    <br />
    <h3>Simple 'a' tag with { generated_link } inside:</h3>
    <a>
      {{ generated_link }}
    </a>
    <br />
    <h3>
      What the Vue variable 'generated_link' is when shown using {
      generated_link }:
    </h3>
    <p>
      {{ generated_link }}
    </p>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      generated_link: "",
    };
  },
  mounted() {
    let route_variables = {
      test: this.$route.query.test,
      test2: this.$route.query.test2,
    };

    if (route_variables["test"] === undefined) {
      console.log(route_variables["test"]);
      route_variables["test"] = "aaaaaahhhhhh";
    }

    var newLink = "https://www.google/?";
    for (const property in route_variables) {
      if (route_variables[property] != undefined) {
        newLink += property + "=" + route_variables[property] + "&";
      }
    }
    this.generated_link = newLink;
  },
};
</script>

<style type="text/css">
body {
  margin: 40px auto;
  max-width: 650px;
  line-height: 1.6;
  font-size: 18px;
  color: #444;
  padding: 0 10px;
}
h1,
h2,
h3 {
  line-height: 1.2;
}
</style>
