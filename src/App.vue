<script setup>
import { reactive } from 'vue';

const data = reactive({
	n1: 0,
	n2: 0,
	result: 0,
	oper: "+",
})

function get_n1(event) {
	data.n1 = event.target.value;
	if (data.n1 == '')  {
    	data.n1 = 0;
  	}
  	data.n1 = parseFloat(data.n1)
  	getCalc();
}

function get_n2(event) {
	data.n2 = event.target.value;
	if (data.n2 == '')  {
    	data.n2 = 0;
  	}
  	data.n2 = parseFloat(data.n2)
  	getCalc();
}

function get_oper(event){
	data.oper = event.target.value;
	getCalc();
}

const getCalc = () => {
  switch(data.oper) {
    case '-':
      return data.result = (data.n1 - data.n2);
    case '+':
      return data.result = (data.n1 + data.n2);
    case '÷':
      if (data.n2 == 0) {
        return data.result = "Indeterminado";
      }
      return data.result = (data.n1 / data.n2);
    case 'x':
      return data.result = (data.n1 * data.n2);
  }
}
</script>

<template>
	<main>
		<form class="text-center">
			<div class="row">
				<div class="col">
					<input required type="number" placeholder="0" class="form-control mb-4" @keyup="get_n1" />
				</div>
				<div class="col-md-2 mb-4 text-center">
					<select class="form-control text-center" @change="get_oper">
						<option class="subtract text-center" value="-">
							<p>-</p>
						</option>
						<option class="add text-center" selected value="+">
							<p>+</p>
						</option>
						<option class="divide text-center" value="÷">
							<p>÷</p>
						</option>
						<option class="multiply text-center" value="x">
							<p>x</p>
						</option>
					</select>
				</div>
				<div class="col">
					<input required type="number" placeholder="0" class="form-control mb-4" @keyup="get_n2" />
				</div>
			</div>
			<div class="row">
				<div class="col">
					<h3>Resultado</h3>
				</div>
			</div>
			<div class="row">
				<div class="col">
					<h2 class="fs-1 fw-bold ps-2">{{ data.result }}</h2>
				</div>
			</div>
		</form>
	</main>
</template>

<style scoped>

</style>
