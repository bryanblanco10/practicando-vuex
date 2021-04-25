<template>
	<div class="container p-3">
		<ul class="list-group">
			<li
				v-for="(item, index) in arrayOrdenado"
				:key="item.id"
				class="list-group-item d-flex justify-content-between align-items-center"
				@click="aumentar(index)"
			>
				{{ item.nombre }}
				<span class="badge badge-primary badge-pill">{{ item.cantidad }}</span>
			</li>
		</ul>
		<button type="button" class="btn btn-danger btn-block mt-3" @click="reiniciar">
			Reiniciar
		</button>
	</div>
</template>
<script>
import { mapState, mapMutations } from "vuex";
export default {
	name: "Lista",
	computed: {
		...mapState(["frutas"]),
		arrayOrdenado(){
			let frutas = this.frutas
			return frutas.sort((a, b) => b.cantidad - a.cantidad)
		}
	},
	methods: {
		...mapMutations(["aumentar", "reiniciar"]),
		// anterior(){
		// 	this.$router.go(-1)
		// },
		// siguiente(){
		// 	this.$router.go(1)
		// }
	},
};
</script>
