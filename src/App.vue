<script>
export default {
  data() {
    return {
      counter: "",
      counter2: "",
      resultC: "",
      movieC: false,
      metka: "",
      tenglik: ""
    }
  },
  methods: {
    decriment(a) {
      if (!this.movieC) this.counter += a
      else {
        if (this.metka) {
          this.counter2 += a
          this.tenglik = "="
          this.result()
        } else {
          this.counter = ""
          this.counter += a
          this.movieC = false
        }
      }
    },

    movie(a) {
      this.movieC = true
      this.metka = a
      if (this.counter2) {
        this.result()
      }
    },

    remove() {
      if (!this.movieC) this.counter = this.counter.slice(0, -1)
      else {
        this.counter2 = this.counter2.slice(0, -1)
        this.result()
      }
    },

    result() {
      switch (this.metka) {
        case "+": {
          this.resultC = +this.counter + +this.counter2
          break
        }
        case "-": {
          this.resultC = +this.counter - +this.counter2
          break
        }
        case "*": {
          this.resultC = +this.counter * +this.counter2
          break
        }
        case "/": {
          this.resultC = +this.counter / +this.counter2
          break
        }
        default: break;
      }
    },
    equal() {
      this.counter = this.resultC
      this.counter2 = ""
      this.resultC = ""
      this.metka = ""
      this.tenglik = ""
    }
  }
}
</script>

<template>
  <div class="card mt-3 mx-auto">
    <div class="card-header bg-dark">
      <h3 class="text-light">{{ counter }} {{ metka }} {{ counter2 }} {{ tenglik }} {{ resultC }}</h3>
    </div>
    <div class="card-body">
      <div class="ishora d-flex justify-content-between mb-3">
        <button class="btn btn-info btn-lg text-light px-4" @click="movie('+')"><b>+</b></button>
        <button class="btn btn-info btn-lg text-light px-4" @click="movie('-')"><b>-</b></button>
        <button class="btn btn-info btn-lg text-light px-4" @click="movie('/')"><b>÷</b></button>
        <button class="btn btn-info btn-lg text-light px-4" @click="movie('*')"><b>x</b></button>
      </div>

      <div class="d-flex justify-content-between">

        <div class="numbers w-100">
          <div class="group-1 w-100 pb-2">
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('7')"
              style="margin-right: 1.5rem;">7</button>
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('8')"
              style="margin-right: 1.5rem;">8</button>
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('9')"
              style="margin-right: 1.5rem;">9</button>
          </div>

          <div class="group-2 pb-2">
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('4')"
              style="margin-right: 1.5rem;">4</button>
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('5')"
              style="margin-right: 1.5rem;">5</button>
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('6')"
              style="margin-right: 1.5rem;">6</button>
          </div>

          <div class="group-3 pb-2">
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('1')"
              style="margin-right: 1.5rem;">1</button>
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('2')"
              style="margin-right: 1.5rem;">2</button>
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('3')"
              style="margin-right: 1.5rem;">3</button>
          </div>

          <div class="group-4">
            <button class="btn btn-lg btn-secondary px-4" @click="decriment('0')"
              style="margin-right: 1.5rem;">0</button>
            <button class="btn btn-lg btn-secondary" @click="remove()" style="margin-right: 1.5rem;">AC</button>
          </div>
        </div>

        <button class="btn btn-white shadow-sm px-4" @click="equal()"><b>=</b></button>

      </div>
    </div>
  </div>

</template>


<style>
.card {
  width: 22rem !important;
  min-height: 70vh;
  /* height: 100vh; */
}
</style>
