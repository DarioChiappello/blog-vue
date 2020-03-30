<template>
	<section id="content">
      <h2 class="subheader">{{ titulo }}</h2>
		<hr/>
		<h1>Nuevo componente creado</h1>
		<h2>{{ subtitulo }}</h2>
		<hr/>

		<h2>Reactividad</h2>
		<input type="text" v-model="nombre" />
		Nombre: <strong>{{nombre}}</strong>

		<h2>Directivas condicionales</h2>
		<input type="number" v-model="edad" />
		Mi edad es: <strong>{{edad}}</strong>

		<p class="alert-success-provisional" v-if="edad && edad >= 18 && edad < 65">Mayor de edad</p>
		<p class="alert-purple-provisional" v-else-if="edad && edad >= 65">Edad avanzada</p>
		<p class="alert-danger-provisional" v-else>Menor de edad</p>

		<h2>Directiva iterativa</h2>
		<ol>
			<li v-for="pelicula in peliculas" :key="pelicula">{{pelicula}}</li>

		</ol>
	</section>
</template>

<script>

export default {
	name: 'MiComponente',
	data() {
		return {
			titulo: 'Mi componente',
			subtitulo: 'Subtitulo del componente',
			nombre: '',
			edad: 18,
			peliculas: ['Harry Potter', 'Bohemian Rhapsody', 'The Godfather','The Lord of the Rings']
		}
	}
}



</script>