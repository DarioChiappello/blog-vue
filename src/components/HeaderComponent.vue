<template>
	<header id="header">
		<div class="center">
			<!-- logo -->
			<div id="logo">
				<img src="../assets/logo.png" class="app-logo" alt="Logotipo">
				<span id="brand">
					<strong>Curso</strong> Vue
				</span>
			</div>
			


			<!-- menu -->
			<nav id="menu">
				<ul>
					<li>
						<router-link to="/home" active-class="active">Inicio</router-link>
					</li>
					<li>
						<router-link to="/blog" active-class="active">Blog</router-link>
					</li>
					<li>
						<router-link to="/formulario" active-class="active">Formulario</router-link>
					</li>
					<li>
						<router-link :to="{name: 'pagina', params: {id: 'Parametro de url'}}" active-class="active">Pagina 1</router-link>
					</li>
					<li>
						<router-link to="/peliculas" active-class="active">Películas</router-link>
					</li>
					
				</ul>
			</nav>
			<!-- Limpiar flotados -->
			<div class="clearfix"></div>	
		</div>
		
	</header>
</template>

<script>
export default {
	name: 'HeaderComponent'
}


</script>