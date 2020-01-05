<template lang="html">
<div >
<h2>Displaying a map</h2>
<p>Description: {{mymap}}</p>
</div>
</template>

<script>

import {mymap} from '../main.js';


export default {
  name: 'Mymap',
  props: ['mymap'],

computed: {
}
};
</script>

<style lang="css" scoped>
</style>
