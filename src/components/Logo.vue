<template>
	<div class="logo" @click="goBack()">
	  <span class="logo__text">
      &larr; Kembali
	    <!-- &larr; {{ $static.metaData.siteName }} -->
	  </span>
	</div>
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<script>
export default {
  methods: {
    goBack () {
      window.history.back();
    }
  }
}
</script>


<style lang="scss">
.logo {
	text-decoration: none;
  color: var(--body-color)!important;
  font-size: .9em;
  cursor: pointer;
  
	&__image {
		vertical-align: middle;
		border-radius: 99px;
		height: 40px;
		width: 40px;
		margin-right: .5em;
	}	
}
</style>