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
    
                    <div v-on:mouseover="changeImageonHover(index)" v-on:click="setCurrentItem(index)" :style="{ backgroundColor: item.color }" id="colorcircle"></div>
    
                </li>
    
            </ul>
    
            <h3>
    
                Selected Item: <span>{{ selectedItem.name }}</span>
    
            </h3>
    
            <!-- Colors -->
    
            <!-- Purchase Section -->
    
    
    
            <button v-on:click="resetAll" id="resetButton">reset</button>
    
            <button v-on:click="addToCart" :disabled="itemAvailable === false">
    
            Add To Cart
    
          </button>
    
        </div>
    
        <!-- Shows the Cart icon togetehr with the Item count -->
    
        <div class="cart">
    
            <!-- Host the shopping cart icon and quantity -->
    
            <div id="priceSection">
    
                <!-- img of cart-->
    
                <img :src="shoppingCart" alt="" srcset="" id="shopping_cart" />
    
                <!-- count -->
    
                <div class="countElement">{{ quantity }}</div>
    
            </div>
    
    
    
            <!-- wil host the price -->
    
            <div id="cost">Total: {{ finalPrice }}</div>
    
        </div>
    
    </div>
</template>

<script>
export default {
    data() {
        return {
            deactivateButton: true,
            image: "src/assets/black_nike.png",
            shoppingCart: "src/assets/shopping_cart.svg",
            //an Items array t allow us to loop through the items and display
            items: [{
                    id: 1,
                    name: "Black Air Max",
                    color: "black",
                    image: "src/assets/black_nike.png",
                    price: 400,
                    currentStockAvailable: 10,
                },
                {
                    id: 2,
                    name: "White Air Max",
                    color: "white",
                    image: "src/assets/white_nike.png",
                    price: 400,
                    currentStockAvailable: 10,
                },
            ],
            quantity: 0,
            selectedItem: {
                index: -1, // if value is negative that means it has not changed
                name: "",
            },
            itemsPurchased: [],
            itemAvailable: true,
            finalPrice: 0,
        };
    },
    methods: {
        changeImageonHover(index) {
            //function is triggered on hover
            if (this.selectedItem.index === -1) {
                this.image = this.items[index].image;
                this.selectedItem.name = "";
            } else {
                this.image = this.items[this.selectedItem.index].image;
            }
        },
        addToCart() {
            console.log(" add to cart has been clicked ");
            // Get the name of the selected item :
            let nameOfItem = this.items[this.selectedItem.index].name;
            // get the current item quantity
            let quantityOfItem = 0;
            //   Reduce the existing quantity form the items  - is the items in stock
            if (this.items[this.selectedItem.index].currentStockAvailable > 0) {
                this.items[this.selectedItem.index].currentStockAvailable -= 1;
                //    Add Item count
                this.quantity += 1;
            } else {
                // Hide deactivate the button
                //     if the items reaches 0 we deactivate the add to card button
                this.itemAvailable = !this.itemAvailable;
            }
            let itemPurchaseObject = {
                name: nameOfItem,
                numberOfItem: this.quantity,
            };
            // Add the item purchase to the itemsPurchased array
            this.itemsPurchased.push(itemPurchaseObject);
            console.log("Product => ", itemPurchaseObject);
            this.calculateFinalPrice();
        },
        // Set the currently selected item
        setCurrentItem(index) {
            this.itemAvailable = true;
            this.quantity = 0;
            this.finalPrice = 0;
            // Creates Selected Item Object
            this.selectedItem.index = index;
            this.selectedItem.name = this.items[index].name;
            //  Updates the current image
            this.image = this.items[index].image;
        },
        calculateFinalPrice() {
            let index = this.selectedItem.index;
            let costPerItem = this.items[index].price;
            this.finalPrice = costPerItem * this.quantity;
        },
        resetAll() {
            this.quantity = 0;
            this.finalPrice = 0;
            this.selectedItem.name = "";
            this.selectedItem.index = -1;
            if (this.itemsPurchased.length > 0) {
                for (let i = 0; i < this.itemsPurchased.length; i++) {
                    this.itemsPurchased[i].name = "";
                    this.itemsPurchased[i].numberOfItem = "";
                }
            }
        },
    },
    mounted() {
        // this.calculateFinalPrice()
    },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200&display=swap");
#myshop {
    display: flex;
}

.countElement {
    font-size: 40px;
    margin: auto;
}

#cost {
    margin-top: 50px;
    padding: 5px;
    font-size: 20px;
    right: 0;
    font-weight: bold;
    color: #ffffff;
    background: #8cdbe2;
    border-radius: 15px;
}

#priceSection {
    display: flex;
    height: min-content;
}

#shopping_cart {
    width: 40px;
    height: 40px;
    margin-left: 20px;
    margin-right: 20px;
    padding: 9px;
    background: #8cdbe2;
    border-radius: 30px;
}

img {
    height: 300px;
    margin-right: 10px;
    border-radius: 50px;
    box-shadow: 0 0 4px rgb(0, 229, 255);
}

#infoSection {
    height: 100%;
    display: grid;
    padding: 33px 60px;
    border-radius: 20px;
    box-shadow: 0 0 4px rgb(0, 229, 255);
}

button {
    background: rgb(2, 117, 102);
}

#colorcircle {
    width: 30px;
    height: 30px;
    border-radius: 50px;
    cursor: pointer;
}

ul,
li {
    list-style: none;
}

h2 {
    font-family: "Poppins", sans-serif;
    font-weight: 100;
}

#resetButton {
    width: auto;
    margin: 10px;
    background: #e90000;
    color: aliceblue;
    font-size: 16px;
    font-weight: bold;
}

.cart {
    padding: 20px;
}
</style>
