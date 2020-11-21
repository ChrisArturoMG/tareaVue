<template>
  <div>
    <input type="text" v-model="texto" class="input">
     {{addItem()}}
      <ol>
        <li v-for="(pro, i) in items" :key="i">
          {{ pro }}
          
        </li>
      </ol>
  </div>
</template>

<script>
export default {
  data: () => { 
    return { 
     texto_nuevo:"",
     texto : "",
     texto2:"",
      items: [],

      sub:"",
      };
  },
  computed:{
    
  },

  methods:  {
    addItem(){  
      console.log("texto   "+this.texto);
      this.texto2 = this.texto;

      if(this.texto2 != this.texto_nuevo){

        for (let index = 0; index < this.texto2.length; index++) {

              if(this.texto2.indexOf(",")>-1 ){
              this.items.push(this.texto2.substring (0,this.texto2.indexOf(",")));
              
              this.sub = this.texto2.substring(0,this.texto2.indexOf(",")+1);
              this.texto2 = this.texto2.replace(this.sub,"")

              console.log("tamanio " + this.texto2.length);
              console.log(this.texto2);
              this.items = this.items.filter((valor, indiceActual   , arreglo) => arreglo.indexOf(valor) === indiceActual);
            }
              this.texto_nuevo = this.texto;
        }
        


              
              

      }

          

    }, 
  }
};
</script>

<style></style>