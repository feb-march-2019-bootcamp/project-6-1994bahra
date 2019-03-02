<template>
<div>
      <div>
            <ul >
                <li v-for="service in services" @click="ActiveLi(service)" :class="{ 'active': service.active}">
              {{service.name}} 
              <span></br>{{service.price  | currency}}</span> </li>
              </br>
			  </br>
			  </br>
            <div class="total"> </br> Total</br> {{total() | currency }} </div>
        </div>
         
        </div>
</template>
<script>
export default {
    
    data:()=>({
    	
        services: [
        	{
        		name: 'Web Development',
        		price: 200,
        		active:false
        	},{
        		name: 'Design',
        		price: 450,
        		active:false
        	},{
        		name: 'Integration',
        		price: 150,
        		active:false
        	},{
        		name: 'Training',
        		price: 300,
        		active:false
        	}
        ]
	}),
	filters:{
		currency(c){
			return '$'+ (c).toFixed(3);
		}
	},
    methods: {
    	ActiveLi(serv){
            serv.active = !serv.active;
    	},
    	total(){

        	 let total = 0.00;

        	this.services.map(x=>{
        		if (x.active){
        			total=total+ x.price;
        		}
        	});

    	   return total;
        }
    }
};
	

</script>

<style scoped>

</style>

