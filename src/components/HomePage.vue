<template>
  <!--Settitng the Base Tag-->
    <h1>NIKE STORE</h1>
  <div id="myshop">
        
        <!--Image-->
        <!-- when using the v-bind declarative, we dont have to state the "v-bind" but we can just use ":" -->
        <img :src="image" alt="Image of nike shoe" />
        <!-- info section -->
        <div id="infoSection">
            <!-- Current Tshirt Color -->
            <h2>Nike Air Force 99</h2>
            <ul v-for="(item, index) in items" :key="item.id">
                <!--{{item.name}}--> 
                <li> 
                    <div v-on:mouseover="changeImageonHover(index)" :style="{backgroundColor:item.color}" id="colorcircle"></div>
                </li>
            </ul>
            <!-- Colors -->
            <!-- Purchase Section -->
            
            <button>Add to Cart</button>
        </div>  
  </div>
</template>

<script>
export default {
    data() {
        return {
            image:"src/assets/black_nike.png",
            //an Items array t allow us to loop through the items and display
            items:[
                { id: 1, name: 'Black Air Max', color: "black", image: "src/assets/black_nike.png", price: 400, currentStockAvailable: 10, },
                { id: 2, name: 'White Air Max', color: "white", image: "src/assets/white_nike.png", price: 400, currentStockAvailable: 10, },
                ],
        };
    },
    methods: {
        changeImageonHover(index){
            //function is triggered on hover
            console.log("index", index )
            this.image = this.items[index].image
            return this.items[index].image

        }   
    },

};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200&display=swap');
   #myshop{
    display: flex;
   } 
  
   img{
    height: 300px;
    margin-right: 10px;
    border-radius: 50px;
    box-shadow: 0 0 4px rgb(0, 229, 255);
   }
   #infoSection{
    height: 100%;
    display: grid;
    padding: 33px 60px;
    border-radius: 20px;
    box-shadow: 0 0 4px rgb(0, 229, 255);
   }
   button{
    background: rgb(2, 117, 102);
   }

   #colorcircle{
    width: 30px;
    height: 30px;
    border-radius: 50px;
    cursor: pointer;
    }
    ul, li{
        list-style: none;
    }
    h2{
        font-family: 'Poppins', sans-serif;
        font-weight: 100;
    }
</style>
