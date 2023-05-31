<template>
    <!-- Contact section start -->
	<section id="contact-section" class="px-12 lg:px-32 py-16 relative">
        <!-- Main text start -->
		<h1 class="uppercase text-5xl mb-4 font-semibold ">
			Try to put our service
		</h1> 
		<!-- Main text end -->

        <!-- Form start -->
        <div class="grid grid-cols-1 md:grid-cols-2 w-full">
            <div class="hidden md:flex justify-center items-center">
                <img src="@/assets/camera.png" alt="">
            </div>
            <div class="flex flex-col w-full items-center">
                <label for="user_nama" class="text-stone-500 text-left">name</label>
                <input type="nama" name="user_nama" id="user_nama" v-model="nama" class="bg-stone-200 py-2 px-4 w-full mb-6 xl:w-1/2">

                <label for="user_email" class="text-stone-500 text-left">email</label>
                <input type="email" name="user_email" id="user_email" v-model="email" class="bg-stone-200 py-2 px-4 w-full mb-6 xl:w-1/2">

                <label for="user_message" class="text-stone-500 text-left">project plan description</label>
                <textarea type="plan" name="user_plan" id="user_plan" v-model="plan" class="bg-stone-200 py-2 px-4 w-full mb-6 xl:w-1/2"></textarea>

                <label for="user_date" class="text-stone-500 text-left">date project</label>
                <input type="date" name="user_date" id="user_date" v-model="project_date" class="bg-stone-200 py-2 px-4 w-full mb-6 xl:w-1/2">

                

                <button class="btn w-full md:w-1/2 " @click="postPemesanan()">Send</button>
            </div>
        </div>
        <!-- Form end -->

        <!-- Circle start -->
        <div class="bg-neutral-200 h-44 w-44 md:h-52 md:w-52 rounded-full absolute -top-20 left-0 mt-16 -z-20"></div>
        <!-- Circle end -->
	</section>
	<!-- Contact section end -->
</template>

<script>
import axios from "axios";

export default {
    name: "ContactSection",
    
    data() {
    return {
      response: "",
      nama: "",
      email: "",
      plan: "",
      project_date: ""
    };
  },

  methods: {
    async postPemesanan() {
      try {
        if (
          this.nama == "" ||
          this.email == "" ||
          this.plan == "" ||
          this.project_date == ""
        ) {
          window.alert("Isi semua data!");
        } else {
          this.response = await axios.post(
            "http://127.0.0.1:8000/api/post-contact",
            {
            //   id_hotel: this.$route.params.id, // ambil id dari parameter
              nama: this.nama,
              email: this.email,
              plan: this.plan,
              project_date: this.project_date
            }
          );

          if (this.response.data.success == true) {
            // success dapat dari hasi response ke API
            // this.$router.push({ path: "" });
            window.alert("Date Telah Berhasil diinputkan");
          } else {
            window.alert(this.response.data.message); // message dapat dari hasi response ke API
          }
        }
      } catch (error) {
        console.log(error);
      }
    },
  }
}
</script>

<style>

</style>