<template>
  <div class="text-center fondo">
    <v-row>
      <v-col v-model="screen">
        <h1 class="cuadro">{{ pantalla }}</h1>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-function </v-icon>
        </v-btn>

        <v-btn @click="c" class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-alpha-c </v-icon>
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-code-less-than </v-icon>
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-percent-outline </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-exponent </v-icon>
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-format-superscript </v-icon>
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-square-root </v-icon>
        </v-btn>

        <v-btn class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-division </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 7"> mdi-numeric-7 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 8"> mdi-numeric-8 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 9"> mdi-numeric-9 </v-icon>
        </v-btn>

        <v-btn @click="por" class="mx-2" fab dark small color="orange darken-2">
          <v-icon dark> mdi-close </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 4"> mdi-numeric-4 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 5"> mdi-numeric-5 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 6"> mdi-numeric-6 </v-icon>
        </v-btn>

        <v-btn
          @click="resta"
          class="mx-2"
          fab
          dark
          small
          color="orange darken-2"
        >
          <v-icon dark> mdi-minus </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 1"> mdi-numeric-1 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 2"> mdi-numeric-2 </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 3"> mdi-numeric-3 </v-icon>
        </v-btn>

        <v-btn
          @click="suma"
          class="mx-2"
          fab
          dark
          small
          color="orange darken-2"
        >
          <v-icon dark> mdi-plus </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn
          :disabled="!neg"
          @click="neg = false"
          class="mx-2"
          fab
          dark
          small
          color="orange darken-2"
        >
          <v-icon dark @click="num = '-'"> mdi-plus-minus-variant </v-icon>
        </v-btn>

        <v-btn @click="num = ''" class="mx-2" fab dark small color="primary">
          <v-icon dark @click="num = 0"> mdi-numeric-0 </v-icon>
        </v-btn>

        <v-btn
          :disabled="!punto"
          @click="punto = false"
          class="mx-2"
          fab
          dark
          small
          color="primary"
        >
          <v-icon dark @click="num = '.'"> mdi-decimal </v-icon>
        </v-btn>

        <v-btn
          @click="igual"
          class="mx-2"
          fab
          dark
          small
          color="green darken-2"
        >
          <v-icon dark @click="sum = 1"> mdi-equal </v-icon>
        </v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'Home',

  data: () => ({
    pantalla: '',
    num: '',
    punto: true,
    neg: true,
    n1: '', // 0
    opera: null,
    flag: 0,
    sum: 0,
    inicio: 0
    // dec: 0
  }),

  computed: {
    screen() {
      // cifra

      if (this.opera == null) {
        // concatenar
        this.concatenar()        
      }

      if (this.opera == 'suma') {
        this.concatenar()
        console.log('ahora sumar')
        //this.pantalla = parseFloat(this.pantalla) + parseFloat(this.num)
        console.log('screen pantalla this.num ', this.pantalla, this.num) // 2 3
        if (this.punto == false) {
          console.log('this.pantalla, this.punto', this.pantalla, this.punto)
          this.punto = true
        } else if (this.sum == 0) {
          // aun no click en =
          // this.pantalla = parseFloat(this.num)  // ojo
          console.log(
            ' sum 0, this.pantalla, this.punto',
            this.pantalla,
            this.punto
          )
        }
      }

      if (this.opera == 'resta') {
        this.concatenar()
        console.log('ahora restar')
        // this.pantalla = this.n1 - this.pantalla // - this.num // 55 - -3 v (transf en negativo) - por - es +
      }

      if (this.opera == 'por') {
        //this.pantalla = ''
        this.concatenar()
        console.log('ahora multiplicar')

        //this.pantalla = parseFloat(this.pantalla) * 1 //parseFloat(this.num) -3 3 (transf en negativo)
        console.log(
          'pantalla this.num this.n1 ',
          this.pantalla,
          this.num,
          this.n1
        )

        //this.igual()
      }

      console.log('pantalla this.num this.n1 ', this.pantalla, this.num, this.n1) // 55 v v
      if (this.num == '-') {
        this.pantalla = this.num
        //this.neg = this.num
      }
      // this.pantalla = parseFloat(this.num)
      //if (this.opera != 'por') {this.num = 0}
    }
  },

  methods: {
    concatenar() {
        console.log('concatenar')

      console.log(' pantalla (+) n1 , num', this.pantalla, this.n1, this.num) // 12 12 1
        if (this.inicio == 1) {
          this.pantalla = this.pantalla + this.num // concatenar // this.pantalla = 0 + parseFloat(this.num)
          console.log('inicio=1 pantalla (+) n1 , num', this.pantalla, this.n1, this.num)
        } else {
          console.log('1º paso')
          //this.n1 = this.pantalla
          this.pantalla = this.n1
          this.inicio = 1
        }
    },

    igual() {
      console.log('igual')
      console.log('this.n1 num this.pantalla', this.n1, this.num, this.pantalla) // 0 3
      this.punto = true
      this.neg = true

      if (this.opera == 'resta') {
        console.log('this.pantalla - n1 ', this.pantalla, this.n1) // -3
        this.pantalla = this.n1 - this.pantalla // parseFloat(this.pantalla) - this.n1 // aca cambia 0
        console.log('this.pantalla igual ', this.pantalla) // 0-3
        this.flag = 0
        // resultado en pantalla restar
      }

      if (this.opera == 'suma') {
        if (this.sum == 0) {
          this.pantalla = 0
        }
        // this.pantalla = 0
        if (this.pantalla == '') {
          this.pantalla = 0
        }
        this.pantalla = parseFloat(this.n1) + parseFloat(this.pantalla) // ok
        this.n1 = 0
        //this.sum = 1 // flag click
        console.log('suma pantalla n1', this.pantalla, this.n1) // 7 0
      }

      if (this.opera == 'por') {
        if (this.pantalla == '') {
          this.pantalla = 1
        }
        this.pantalla = parseFloat(this.num) * parseFloat(this.pantalla)
        this.n1 = 0
        console.log('por pantalla n1', this.pantalla, this.n1)
      }

      // alert()

      //this.n1 = this.pantalla
    },

    suma() {
      this.opera = 'suma'
      this.punto = true
      this.inicio = 0
      //this.neg = true

      console.log('suma this.n1 ', this.n1) // vacio

      this.n1 = parseFloat(this.pantalla) // 0+5 parseFloat(this.n1) + 
      console.log('n1 + pantalla ', this.n1, this.pantalla) // 0.5  0.5
      this.pantalla = this.n1 // 0.5
      // this.igual()
    },

    resta() {
      this.opera = 'resta'
      this.punto = true
      this.inicio = 0
      //this.neg = true
      this.n1 = this.pantalla

      console.log('resta this.n1 ', this.n1)
      console.log('flag = ', this.flag)

      if (this.flag == 1) {
        console.log('flag 1 ')
        this.n1 = this.n1 - parseFloat(this.pantalla)
        console.log('n1 - this.pantalla', this.n1, this.pantalla)
        console.log('this.igual()')
        // this.igual()
      } else {
        console.log('flag 0 ')
        console.log('this.pantalla - n1 ', this.pantalla, this.n1) // ok
        //this.n1 = parseFloat(this.pantalla) - this.n1

        this.flag = 1
        // this.igual()
      }
    },

    por() {
      // this.op() this.punto = true this.neg = true
      this.opera = 'por'
      this.punto = true
      this.inicio = 0
      //this.neg = true

      this.n1 = 1

      console.log('por this.n1 this.pantalla', this.n1, this.pantalla) // 3 1

      this.n1 = this.n1 * parseFloat(this.pantalla) // 3*1
      console.log('n1  pantalla ', this.n1, this.pantalla) // 3 3
      this.pantalla = this.n1
    },

    c() {
      this.pantalla = ''
      this.opera = null
      this.n1 = ''
      this.flag = 0
      this.inicio = 0
      this.neg = true
      this.punto = true
    }
  }
}
</script>

<style scoped>
.cuadro {
  border: 2px solid black;
  height: 50px;
}
.fondo {
  background: grey;
}
</style>
