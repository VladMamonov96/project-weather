<script setup>
const {color = 'white', size = 50} = defineProps({color: String, size: Number})
</script>

<template>
<!--  <svg   width="50px" height="50px" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" version="1.1" fill="none" :stroke="color" stroke-linecap="round" stroke-linejoin="round" stroke-width="1">-->
<!--    <circle cy="8" cx="8" r="3.25"/>-->
<!--    <path d="m2.75 13.25.5-.5m9.5 0 .5.5m-.5-10 .5-.5m-10 .5-.5-.5m-.50 5.25h-1m13.5 0h-1m-5.75 5.75v1m0-13.5v1"/>-->
<!--  </svg>-->
<!--  -->
  <svg width="50px" height="50px" :style="{scale: size / 50}" viewBox="-0.5 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M17.93 15.745H6.87C4.45 15.745 2.5 13.725 2.5 11.215C2.5 8.72503 4.45 6.68503 6.87 6.68503C7.4 6.68503 7.89999 6.77503 8.35999 6.95503C8.60999 7.04503 8.87001 6.95503 9.01001 6.73503C9.74001 5.49503 11.07 4.65503 12.59 4.65503C14.61 4.65503 16.28 6.11503 16.69 8.06503C16.75 8.33503 16.97 8.47504 17.24 8.41504C17.46 8.36504 17.69 8.34503 17.93 8.34503C19.91 8.34503 21.5 10.005 21.5 12.055C21.51 14.095 19.91 15.745 17.93 15.745Z" :stroke="color" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M10.51 20.345L12.01 17.745" :stroke="color" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M14.51 20.345L16.01 17.745" :stroke="color" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M6.51001 20.345L8.01001 17.745" :stroke="color" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
</template>
