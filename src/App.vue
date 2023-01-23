<script >
  export default{
   data(){
    return{
      datasensor:"",
      datasensor2:"100"
    }
   },
   created(){
    // this.getData()
   },
   methods:{
    // getData(){
    //   alert("HELLO");
    // },
    // getData2(){
    //   alert("HELLO 2");
    // },
    async ubah (){
      const dataku = await fetch("http://localhost:82/sensor1")
      const datajson = await dataku.json()
      console.log(datajson)
      this.datasensor = datajson.sensor
      console.log(this.datasensor)
    }
   }
  }
</script>

<template>
  <body>
    <div class=" w-1/4 justify-center flex items-center mt-24"> 
    hello Mujahidin Syamil Kaffah
    <button @click="ubah" class="ml-1 bg-cyan-700 p-2 rounded-full hover:bg-slate-900 font-semibold text-white">ambil data</button>
    </div>
  <div class="mt-3">
    <table class="border-collapse border border-slate-500 bg-zinc-400 uppercase">
      <tr>
        <td class="border border-black p-3 items-center cursor-pointer hover:bg-slate-500 hover:text-white">Tanggal</td>
        <td class="border border-black p-3 justify-center cursor-pointer hover:bg-slate-500 hover:text-white"> Lokasi </td>
        <td class="border border-black p-3 flex justify-center cursor-pointer hover:bg-slate-500 hover:text-white"> Suhu </td>
        <td class="border border-black p-3 justify-center cursor-pointer hover:bg-slate-500 hover:text-white"> Kondisi </td>
      </tr>
      <tr v-for ="i in datasensor">
        <td class="border border-black p-3 cursor-pointer hover:bg-slate-500 hover:text-white">{{ i.tanggal }}</td>
        <td class="border border-black p-3 cursor-pointer hover:bg-slate-500 hover:text-white">{{i.lokasi}}</td>
        <td class="border border-black p-3 cursor-pointer hover:bg-slate-500 hover:text-white">{{i.suhu}}</td>
        <td class="border border-black p-3 cursor-pointer hover:bg-slate-500 hover:text-white">{{i.kondisi}}</td>
      </tr>
    </table>
  </div>
  </body>
</template>



