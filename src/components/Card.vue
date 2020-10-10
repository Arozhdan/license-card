<template>
	<div class="card">

		<div class="license-type " :class="{license__active: active===1 }">
			<label class="container" @click="active=1"> <span class="license-type-data">Licence plan #1 </span>
				<input type="radio" checked="checked" name="radio">
				<span class="checkmark"></span>
			</label>
			<span class="license-price">$13 per license</span>
		</div>

		<div class="license-type" :class="{license__active: active===2 }">
			<label class="container" @click="active=2"> <span class="license-type-data">Licence plan #2 </span>
				<input type="radio" name="radio">
				<span class="checkmark"></span>
			</label>
			<span class="license-price">$22 per license</span>
		</div>

		<div class="license-type" :class="{license__active: active===3 }">
			<label class="container" @click="active=3"> <span class="license-type-data">Licence plan #2 </span>
				<input type="radio" name="radio">
				<span class="checkmark"></span>
			</label>
			<span class="license-price">$34 per license</span>

		</div>
		<div class="card-quantity">
			<label for="quantity">Number of clients:</label>
			<select name="quantity" id="quantity" v-model="amount" >
				<option value="1">1</option>
				<option value="2">2</option>
				<option value="3">3</option>
				<option value="4">4</option>
				<option value="5">5</option>
				<option value="6">6</option>
				<option value="7">7</option>
				<option value="8">8</option>
			</select>
		</div>
		<div class="card-price">
			<h2 class="card-price-heading">total: <span>$ {{ calculate }}<sup>US</sup></span></h2>
			<button class="btn btn__card" @click="show=true">buy now</button>
			<p class="card-selected">Selected plan : #{{active}}</p>
		</div>
		<div class="card-modal" v-if="show">
			<div class="card-modal-inner">
				<h2 class="card-modal-title">Your order</h2>
				<h2 class="card-modal-title">{{calculate}} $</h2>
				<p class="card-modal-cost">You have ordered {{amount}} of licenses #{{active}} </p>
				<button class="btn" @click="show=false">Proceed</button>
				<button class="btn-close" @click="show=false">x</button>

			</div>
		</div>
		</div>
</template>

<script>
    export default {
        name: "Card",
        data: () => ({
            active: 1,
		        amount:1,
		        show:false
        }),
		    computed:{
            calculate(){
                if (this.active===1){
                    return this.amount*13
                }

                if (this.active===2){
                    return this.amount*22
                }

                if (this.active===3){
                    return this.amount*34
                }
                return null
            }
		    },

    }
</script>

<style scoped>

</style>