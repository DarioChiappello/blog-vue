<template>
<div class="general">
	<Slider texto="Página de pruebas"></Slider>
    <div class="center">
	<section id="content">
			<h2 class="subheader">Página de pruebas</h2>
			<h3>{{id_desde_url}}</h3>
			<button @click="actualizarNombre()">Actualizar nombre</button>
			<button @click="redirigirAlBlog()">Redirigir al blog</button>
			<h4>{{nombre}}</h4>
	</section>
	<Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
</div>
</template>
<script>
import Slider from './Slider.vue';
import Sidebar from './Sidebar.vue';
export default {
	name: 'Página',
	components: {
    Slider,
    Sidebar    
  },
	mounted(){
		this.id_desde_url = this.$route.params.id;
	},
	updated(){

	},
	data(){
		return{
			id_desde_url: null,
			nombre: 'Darío Chiappello'
		};
		
	},
	methods:{
		actualizarNombre(){
		this.nombre = 'Darío Andrés Chiappello';
		},
		redirigirAlBlog(){
			this.$router.push('/blog');
		}
	}
	
}
</script>