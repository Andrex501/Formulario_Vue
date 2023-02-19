
<script setup>

import {ref} from 'vue'

let nombre = ref("")
let apellido = ref("")
let correo = ref("")
let contraseña = ref("")
let mensaje3 =ref("Campos exitosos, en un momento empezaremos.")
let cambiocolor = ref()
let pintar = ref("")



function verificar() {


let expresion =  /^\w+([.-_+]?\w+)*@\w+([.-]?\w+)*(\.\w{2,10})+$/ 
let verifi = expresion.test(correo.value)
//  nombre.value.trim()===''
// nombre.trim().length<8

if ( nombre.value.trim()===''  ) {
  pintar.value = "Debes llenar el campo Nombre"
  cambiocolor.value = "background-color:#ff4d4d;"
  setTimeout(() => {
    cambiocolor.value = ""
  pintar.value = ""
 }, 3000);
}


else if ( apellido.value.trim()===''  ) {
  pintar.value = "Debes llenar el campo Apellido "
  cambiocolor.value = "background-color:#ff4d4d;"
  setTimeout(() => {
    cambiocolor.value = ""
  pintar.value = ""
 }, 3000);
}


else if ( verifi  == false ) {
  pintar.value = "Debes llenar el campo correo (Debe contener @ y .com en su respectivo orden)"
  cambiocolor.value = "background-color:#ff4d4d;"
  setTimeout(() => {
    cambiocolor.value = ""
  pintar.value = ""
  correo.value = ""
 }, 3000);
}


else if (contraseña.value.trim().length<8 ||contraseña.value.trim()===''  ) {
  pintar.value = "Debes llenar el campo contraseña (Minimo 8 digitos)"
  cambiocolor.value = "background-color:#ff4d4d;"
  setTimeout(() => {
    cambiocolor.value = ""
  pintar.value = ""
  contraseña.value = ""
 }, 3000);
}



else{
  pintar.value = mensaje3.value
  cambiocolor.value = "background-color:#55efc4;"
  setTimeout(() => {
  cambiocolor.value = ""
  pintar.value = ""
 },3000);
}


}



function cambiocontra() {
  
 let contr =  document.getElementById("contraseña")
 if (contr.type == "password" ) {
  contr.type = "text"
 }else{
  contr.type = "password"
 }
  
}

</script>



<template  >
<div>

<div style="background-color:#d1d8e0;" class="container-fluid">

  <div style="height: 100%; padding-top: .5%; padding-bottom: 2%;  " class="row">

  <div  class="col-sm-4"></div>
  <div  style=" border-radius: 10px; box-shadow: 6px 6px 6px 6px  #535c68 ;  height: 100%;  background-image: url(https://png.pngtree.com/thumb_back/fh260/back_our/20190620/ourmid/pngtree-purple-beautiful-romantic-cool-fresh-banner-background-image_156587.jpg);" class="col-sm-4">

  <center>
    <img style="height: 200px; width: 200px; border-radius: 100px;" src="./silueta.png" alt="">
  </center>
<br>
<center>
  <b style="color: #fff; font-size: 18px;" >FORMULARIO</b>
</center>

   <div style=" height: 410px; width: 100%; margin-top: 2%; margin-bottom: 2%;border-radius: 10px; background-color: #dfe6e9;" >
  
<br>

<div style="width: 90%; margin-left: 3%;" class="input-group mb-3">
  <input style="padding: 8px;" 
  type="text" class="form-control" 
  placeholder="Ingrese su nombre" 
  aria-label="Recipient's username" 
  aria-describedby="button-addon2" 
  v-model="nombre">
</div>
  
 

<div style="width: 90%; margin-left: 3%;" class="input-group mb-3">
  <input style="padding: 8px;" 
  type="text" class="form-control" 
  placeholder="Ingrese su apellido" 
  aria-label="Recipient's username" 
  aria-describedby="button-addon2" 
  v-model="apellido">
</div>


<div style="width: 90%; margin-left: 3%;" class="input-group mb-3">
  <input style="padding: 8px;" 
  type="email" class="form-control" 
  placeholder="Ingrese su correo electronico" 
  aria-label="Recipient's username" 
  aria-describedby="button-addon2" 
  v-model="correo">
</div>



<div style="width: 90%; margin-left: 3%;" class="input-group mb-3">
  <input style="padding: 8px;" 
  type="password" class="form-control" 
  id="contraseña"
  placeholder="Ingrese su contraseña" 
  aria-label="Recipient's username" 
  aria-describedby="button-addon2" 
  v-model="contraseña">
  <button  @click="cambiocontra()" class="btn btn-outline-primary" type="button" id="button-addon2"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-eye-fill" viewBox="0 0 16 16">
  <path d="M10.5 8a2.5 2.5 0 1 1-5 0 2.5 2.5 0 0 1 5 0z"/>
  <path d="M0 8s3-5.5 8-5.5S16 8 16 8s-3 5.5-8 5.5S0 8 0 8zm8 3.5a3.5 3.5 0 1 0 0-7 3.5 3.5 0 0 0 0 7z"/>
</svg></button>
</div>



<br><br>

<center>
  <button style="padding: 10px;" @click="verificar()" class="btn btn-primary"> INICIAR SESIÓN </button>
</center>

<div style="margin-top: 22px;" >
  <div v-bind:style="cambiocolor" style="height: 40px; border-radius: 10px ;display: flex; justify-content: center; align-items: center;  " >
  {{ pintar }}
  </div>
</div>
  

</div>



</div>
<div  class="col-sm-4"></div>
</div>
</div>
</div>
</template>

