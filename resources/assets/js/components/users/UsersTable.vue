<template>
	<div>
		<router-link :to="{name: 'create'}" class="btn btn-success mb-3">
			Add user
			<i class="fas fa-plus"></i>
		</router-link>
		<div class="table-responsive-md">
			<table class="table">
				<thead>
					<tr>
					  <th scope="col">ID</th>
					  <th scope="col">First Name</th>
					  <th scope="col">Last Name</th>
					  <th scope="col">Email</th>
					  <th scope="col">Actions</th>
					</tr>
				</thead>
				<tbody>
					<user-row @userRemoved="removeUser" v-for="(user, index) in users" :user="user" :index="index" :key="user.id"></user-row>
				</tbody>
			</table>
		</div>
	</div>
</template>

<script>
	import UserRow from './UsersRow.vue';

	export default {
		data(){
			return {
				users: []
			}
		},
		mounted(){
			axios.get('/api/users').then((response) => {
				this.users = response.data;
			});
		},
		notifications: {
            showSuccessMsg: {
              type: 'success',
              title: 'User deleted',
              message: 'The user has been deleted successfully'
            }
        },
		components: {
			UserRow
		},
		methods: {
		    removeUser(index){
		        this.showSuccessMsg();
		        this.users.splice(index, 1);
			}
		}
	}
</script>

<style>
	
</style>