<template>
   <div class="product product_horizontal" >                           
        <span class="product_code">{{ product.code }}</span>
            <div class="product_status_tooltip_container">
                <span class="product_status">Наличие</span>
            </div>                                
            <div class="product_photo">
                <a href="#" class="url--link product__link">
                    <img :src = ImageUrl>
                </a>                                    
            </div>
            <div class="product_description">
                <a href="#" class="product__link">{{ product.title }}</a>
            </div>
            <div class="product_tags hidden-sm">
                <p>Могут понадобиться:</p>
                <a class="url--link">{{ product.assocProducts }}</a>
            </div>
            <div class="product_units">
            <div class="unit--wrapper">
                <div class='unit--select' :class="{ 'unit--active':  isActiveMeter }">
                    <p class="ng-binding" @click="inMeter()">За м. кв.</p>
                </div>
                <div class='unit--select' :class="{ 'unit--active':  isActivePackaging }">
                    <p class="ng-binding" @click="inPackaging()">За упаковку</p>
                </div>
            </div>
        </div>
        <p class="product_price_club_card">
            <span class="product_price_club_card_text">По карте<br>клуба</span>
            <span class="goldPrice">{{ (goldPrice * stepCounter).toFixed(2) }}</span>
            <span class="rouble__i black__i">
                <svg version="1.0" id="rouble__b" xmlns="http://www.w3.org/2000/svg" x="0" y="0" width="30px" height="22px" viewBox="0 0 50 50" enable-background="new 0 0 50 50" xml:space="preserve">
                    <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#rouble_black"></use>
                </svg>
            </span>
        </p>
        <p class="product_price_default">
            <span class="retailPrice">{{ (retailPrice * stepCounter).toFixed(2) }}</span>
            <span class="rouble__i black__i">
                <svg version="1.0" id="rouble__g" xmlns="http://www.w3.org/2000/svg" x="0" y="0" width="30px" height="22px" viewBox="0 0 50 50" enable-background="new 0 0 50 50" xml:space="preserve">
                    <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#rouble_gray"></use>
                </svg>
            </span>
        </p>
        <div class="product_price_points">
            <p class="ng-binding">Можно купить за 231,75 балла</p>
        </div>
        <div class="list--unit-padd"></div>
        <div class="list--unit-desc">
            <div class="unit--info">
                <div class="unit--desc-i"></div>
                <div class="unit--desc-t">
                    <p>
                        <span class="ng-binding">Продается упаковками:</span>
                        <span class="unit--infoInn">1 упак. = 2.47 м. кв. </span>
                    </p>
                </div>
            </div>
        </div>
        <div class="product__wrapper">
            <div class="product_count_wrapper">
                <div class="stepper">
                    <input class="product__count stepper-input" type="text" :value = stepCounter>
                    <span class="stepper-arrow up" @click="stepUp()"></span>
                    <span class="stepper-arrow down" @click="stepDown()"></span>                                            
                </div>
            </div>
            <span class="btn btn_cart" data-url="/cart/" :data-product-id = product.productId >
                <svg class="ic ic_cart">
                    <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#cart"></use>
                </svg>
                <span class="ng-binding">В корзину</span>
            </span>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Product',
        props: {
            product: Object, 
        },
        data() {
            return {
                goldPrice: this.product.priceGoldAlt,
                retailPrice:  this.product.priceRetailAlt,
                isActiveMeter: true,
                isActivePackaging: false,
                stepCounter: 1,
                ImageUrl: this.product.primaryImageUrl.slice(0, -4) + '_220x220_1.jpg',
            }
        },
        methods: {
            inMeter() {
                this.isActiveMeter = true;
                this.isActivePackaging = false;
                this.goldPrice = this.product.priceGoldAlt;
                this.retailPrice = this.product.priceRetailAlt;
            },

            inPackaging() {
                this.isActiveMeter = false;
                this.isActivePackaging = true;
                this.goldPrice = this.product.priceGold;
                this.retailPrice = this.product.priceRetail;
            },

            stepUp() {
                this.stepCounter++;
            },
            
            stepDown() {
                if (this.stepCounter > 1) {
                    this.stepCounter--;
                }
            }
        }
    }
</script>

<style scoped>
</style>