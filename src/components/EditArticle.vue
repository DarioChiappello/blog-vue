<template src="./CreateArticle.html"></template>
<script>

import Sidebar from './Sidebar.vue';
import Article from '../models/Article';
import axios from 'axios';
import { Global } from '../Global';
import { required } from 'vuelidate/lib/validators';
import swal from 'sweetalert';


export default {
	name: 'EditArticle',
	components: {
		Sidebar
	},
	data(){
		return {
			url: Global.url,
			file: '',
			article: new Article('', '', null, ''),
			submitted: false,
			isEdit: true
		};
	},
	validations: {
		article: {
			title: {
			required
		},
		content: {
			required
		}
		}

		
	},
	mounted(){

	var articleId = this.$route.params.id;
	this.getArticle(articleId);
	},
	methods: {
		fileChange(){
			this.file = this.$refs.file.files[0];
			console.log(this.file);
		},
		getArticle(articleId){
			axios.get(this.url+ 'article/'+ articleId)
				.then(res =>{
					if(res.data.status == 'success'){
						this.article = res.data.article;
					}
				});
		},
		save(){
			
			this.submitted = true;
			var articleId = this.$route.params.id;

			this.$v.$touch();
			if(this.$v.$invalid){
				return false;
			} else {
				



				axios.put(this.url+'article/'+ articleId, this.article)
				.then(response => {
					if(response.data.status == 'success'){
						
						//Subida de imagen
						if(this.file != null && this.file != undefined && this.file != ''){
							const formData = new FormData();

							formData.append(
								"file0",
								this.file,
								this.file.name
							);

							var articleId = response.data.article._id;

							axios.post(this.url + "upload-image/" + articleId, formData)
								.then(response => {
									if (!response.data.article) {
										
										swal(
											'Artículo editado',
											'El artículo se ha editado con éxito',
											'success'
										);

										this.article = response.data.article;
										this.$router.push('/articulo/'+this.article._id);
										
									} else {
										//mostrar alert error
										swal(
											'Artículo fallido',
											'El artículo no se ha editado con éxito',
											'error'
										);
										
									}
								})
								.catch(error => {
									console.log(error);
								});
						}else{
							
							swal(
											'Artículo editado',
											'El artículo se ha editado con éxito',
											'success'
										);

							this.article = response.data.article;
							this.$router.push('/articulo/'+this.article._id);
						}			
					}
				})
				.catch(error => {
					console.log(error);
				});
			}

			
		}
	}
}
</script>