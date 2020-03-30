<template>
<div class="general">
	
    <div class="center">
	<section id="content">
			<h1 class="subheader">Películas</h1>
			<div class="favorita" v-if="favorita">
				<h3>{{favorita.title}} ha sido añadida como favorita</h3>
			</div>
			
			<div id="articles">
				<!---->
				<div v-for="pelicula in peliculasMayuscula" v-bind:key="pelicula.title">
				<Pelicula
					:pelicula="pelicula"
					v-on:favorita="haLlegadoLaPeliculaFavorita" ></Pelicula>
				</div>

			</div>
			
		</section>
		<Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
</div>

</template>
<script>
import Sidebar from './Sidebar.vue';
import Pelicula from './Pelicula.vue';

export default {
	name: 'Peliculas',
	components: {
		Pelicula,
		Sidebar
	},
	methods: {
		haLlegadoLaPeliculaFavorita(favorita){
			this.favorita = favorita;
		}
	},
	filters: {
		mayusculas(value){
			return value.toUpperCase();
		}
	},
	computed: {
		peliculasMayuscula(){
			var peliculasMod = this.peliculas;
			for(var i = 0; i < this.peliculas.length; i++){
				peliculasMod[i].title = peliculasMod[i].title.toUpperCase();
			}

			return peliculasMod;
		}
	},
	data(){
		return {
			favorita: null,
			peliculas: [
				{title: 'Bohemian Rhapsody', year: 2018, image: "https://dam.empireonline.com.mx/wp-content/uploads/2018/11/bohemian-rhapsody-pelicula-freddie-mercury-sinopsis.jpg"},
				{title: 'The Godfather', year: 1972, image: "https://bucket3.glanacion.com/anexos/fotos/36/3101436.jpg"},
				{title: 'Harry Potter y las Reliquias de la Muerte', year: 2011, image: "https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSEkYV2vLuJ58LWWJO3IPXQMXpoBqdYcBmMEku_HY-Im2kcJ5J0"}
			]
		}
	}
}
</script>