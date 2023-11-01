<template>
	<h1>add</h1>
	<ContactForm  :contact="contact"  @create:contact="createCt"/>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
	components: {
		ContactForm
	},
	data() {
		return {
			contact: null,
			message: "",

		};
	},
	methods: {
		async createCt(data){
			console.log(data)
			try {
				this.status = await ContactService.create(data);
				this.$router.push({ name: "contactbook" });


			} catch (error) {
				console.log(error)
			}
		},
	}
}
</script>