<template>
	<div class="vue-component">
		<NavbarPath :items="currentGroup.path"/>
		<p>
			<button
				:disabled="currentGroupIsRoot"
				@click="loadGroup(currentGroup.parent_id)"> 
				&larr;
			</button>
			<button @click="$emit('add-group')"> + add group </button>
			<button @click="$emit('add-screen')"> + add screen </button>
		</p>
	</div>
</template>

<script>
import Vuex from 'vuex';
import NavbarPath from './NavbarPath';

export default {
	components: {
		NavbarPath
	},
	computed: {
		currentGroupIsRoot() {
			return this.currentGroup.path.length == 1;
		},
		// Vuex state
		...Vuex.mapState(['currentGroup'])
	},
	methods: {
		// Vuex actions
		...Vuex.mapActions(['loadGroup'])
	}
}
</script>
