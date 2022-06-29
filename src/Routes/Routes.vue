<script>
import PATHS from "./paths";
import Page1 from "../views/Page1.vue";
import Page2 from "../views/Page2.vue";
import Page2Error from "../views/Page2Error.vue";
import Page3 from "../views/Page3.vue";

const routes = [
  {
    pathname: PATHS.PAGE_1,
    component: Page1,
    isDefault: true,
  },
  {
    pathname: PATHS.PAGE_2,
    component: Page2,
  },
  {
    pathname: PATHS.PAGE_2_ERROR,
    component: Page2Error,
  },
  {
    pathname: PATHS.PAGE_3,
    component: Page3,
  },
];

export default {
  data() {
    return {
      pathname: window.location.pathname,
    };
  },
  computed: {
    page() {
      const page = routes.find((item) => item.pathname === this.pathname);
      return page ? page.component : null;
    },
    defaultPage() {
      return routes.find((item) => item.isDefault);
    },
  },
  mounted() {
    const resources = Object.values(PATHS);
    if (resources.findIndex((pathname) => pathname === this.pathname) === -1)
      window.location.pathname = this.defaultPage.pathname;
  },
};
</script>

<template>
  <component :is="page" />
</template>
