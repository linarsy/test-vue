<template>
	<div id="app">
    <div class="container">
		  <FieldText/>
    </div>
    <p>Валидация происходит при потере фокуса. Валидное значение не менее 8 символов.</p>
	</div>
</template>

<script>
import FieldText from './components/FieldText.vue'

export default {
	components: {
		FieldText,
	}
}
</script>

<style lang="scss">
@import './variables.scss';

*, *::before, *::after {
	box-sizing: border-box;
}

#app {
	max-width: 400px;
	margin: 50px auto;
	font-family: Arial, Helvetica, sans-serif;
	color: $vue-blue;
}

.container {
  max-width: 272px;
}

</style>