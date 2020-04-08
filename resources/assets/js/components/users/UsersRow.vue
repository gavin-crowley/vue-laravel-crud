<template>
	<tr>
      <th scope="row">{{ user.id }}</th>
      <td>{{ user.first_name }}</td>
      <td>{{ user.last_name }}</td>
      <td>{{ user.email }}</td>
      <td>
          <router-link :to="editUserUrl" class="btn btn-warning text-white">Edit</router-link>
      	<button @click='confirmBeforeDelete' type="button" class="btn btn-danger">Delete</button>
      </td>
    </tr>
</template>

<script>
	export default {
		props: {
			user: {
				type: Object
			},
      index: Number
		},

    computed: {
		  editUserUrl(){
		    return `/user/${this.user.id}`;
      }
    },

    notifications: {
      showErrorMsg: {
        type: 'error',
        title: 'Something went wrong',
        message: 'Something happend deleting the user, try again later'
      }
    },

    methods: {
	    deleteUser(){
        axios.delete(`/api/users/${this.user.id}`).then((resp) =>{
          this.$emit('userRemoved', this.index);
        })
        .catch((resp) => {
          this.showErrorMsg();
        });
      },

      confirmBeforeDelete(){
        var app = this;
        this.$swal({
          title: "Are you sure?",
          text: "This user will be deleted permanently from the system",
          icon: "warning",
          buttons: true,
          dangerMode: true
        })
        .then((willDelete) => {
          if(willDelete){
             app.deleteUser();
          }
        })
      }
    }
	}
</script>