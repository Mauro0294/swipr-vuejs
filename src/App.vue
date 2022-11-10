<script>
import home from "./home.vue";
import favorietenPage from "./favorieten.vue";

const routes = {
	"/": home,
	"/favorieten": favorietenPage,
};

export default {
	data() {
		return {
			currentPath: window.location.hash,
		};
	},
	computed: {
		currentView() {
			return routes[this.currentPath.slice(1) || "/"] || favorietenPage;
		},
	},
	mounted() {
		this.currentPath = window.location.pathname;
	},
};
</script>

<template>
  <component :is="currentView" />
</template>
