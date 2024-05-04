<template>
  <div class="background">
    <img src="https://i.ibb.co/Kwp1KRL/dashboard-3510327-1280-1.jpg" />
  </div>
  <div>
    <h1 :class="titleClass" style="margin-left: 10px; color: white; font-weight: bold;">Komentar</h1>
    <p :style="paragraphStyle" style="margin-left: 10px; color: white;">Berikan komentar Anda Untuk Memberikan Kami Perubahan.</p>
    <div style="border-bottom: 1px solid white; margin-bottom: 20px;"></div>

    <div class="mb-3" style="margin-left: 10px;color: white;">
      <label for="name" class="form-label" style="color: white;">Nama:</label>
      <input type="text" v-model="name" class="form-control" :style="[inputStyle, { backgroundColor: 'transparent', color:'white' }]">
    </div>
    <div class="mb-3" style="margin-left: 10px;color: white;">
      <label for="email" class="form-label" style="color: white;">Email:</label>
      <input type="email" v-model="email" class="form-control" :style="[inputStyle, { backgroundColor: 'transparent',color:'white' }]">
    </div>
    <div class="mb-3" style="margin-left: 10px;color: white;">
      <label for="comment" class="form-label" style="color: white;">Komentar:</label>
      <textarea v-model="comment" class="form-control" :style="[inputStyle, { backgroundColor: 'transparent', color:'white' }]" rows="5"></textarea>
    </div>
    <button @click="submitForm" class="btn btn-primary" :class="buttonClass" style="margin-left: 10px;">Kirim</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Swal from 'sweetalert2';

const name = ref('');
const email = ref('');
const comment = ref('');

const submitForm = () => {
  const senderInfo = `Nama: ${name.value}\nEmail: ${email.value}`;
  Swal.fire({
    title: 'Apakah Anda ingin melanjutkan?',
    text: senderInfo,
    icon: 'question',
    showCancelButton: true,
    confirmButtonText: 'Ya',
    cancelButtonText: 'Tidak'
  }).then((result) => {
    if (result.isConfirmed) {
      Swal.fire('Sukses!', 'Komentar Anda telah dikirim.', 'success');
    }
  });
};

const titleClass = 'title'; 
const paragraphStyle = {
  fontSize: '16px',
  color: 'blue'
};
const inputStyle = { 
  maxWidth: '300px'
}; 
const buttonClass = 'button';
</script>

<style scoped>
.background img{
  position: fixed;
  top: 0;
  left: 0;
  min-height: 90%;
  min-width: 1500px;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: -2;
  object-fit: cover;
  -webkit-background-size:cover; -moz-background-size:cover; -o-background-size:cover; background-size: cover;
  filter: brightness(0.8);
}

</style>
