<template>
<div class="superContainer">
        <img 
          @click="menu = true"
          class="hamburgerIcon hidden-sm-and-up"
          height="15"
          v-if="!menu" 
          src="../assets/icon-hamburger.svg"
          >
          <span class="mobileTitle hidden-sm-and-up" v-if="!menu">room</span>
        <div v-if="menu">
            <div class="mob-navigation">
                <v-list light class="navigation-tabs d-inline-block mt-5">
                    <v-list-item class="mr-n3"> <v-img @click="menu = false" class="closeButton" src="../assets/icon-close.svg"></v-img> </v-list-item>
                    <v-list-item class="mr-3">home</v-list-item>
                    <v-list-item class="mr-3">shop</v-list-item>
                    <v-list-item class="mr-3">about</v-list-item>
                    <v-list-item>contact</v-list-item>
                </v-list>
            </div>
        </div>
    <div class="container">
        <div class="flex1">
            <div class="navigation">
                    <v-list class="navigation-tabs d-inline-block" dark>
                        <v-list-item>room</v-list-item>
                        <v-list-item>home</v-list-item>
                        <v-list-item>shop</v-list-item>
                        <v-list-item>about</v-list-item>
                        <v-list-item>contact</v-list-item>
                    </v-list>
                </div>
                <img class="top-image" :src="currentSlide.picture">
        </div>
        <div class="flex2">
            <h1 class="slider-header">{{currentSlide.header}}</h1>
               <div class="content-wrap">
                    <span class="slider-content">{{currentSlide.content}}</span>
               </div>
               <div class="shop-now">
                   <span class="shop-text mr-5">SHOP NOW</span> <img class="shop-now-img" width="70" src="../assets/icon-arrow.svg">
               </div>
               <div class="btn-wrapper">
                <button @click.stop="slidePrev"><v-img width="15" src="../assets/icon-angle-left.svg"></v-img></button> <button  @click="slideNext"><v-img width="15" src="../assets/icon-angle-right.svg"></v-img></button>
               </div>
        </div>
        </div>
        <div class="layout">
            <div class="flex3">
                <img  src="../assets/image-about-dark.jpg">
            </div>
            <div class="flex4">
                <h5 class="about-header mt-14 ">ABOUT OUR FURNITURE</h5>
                <p class="about-content">
                    Our multifunctional collection blends design and function to suit your individual taste. Make each room unique, or pick cohesive theme that best express your interests and what inspire you.
                    Finde furniture pieces, from traditional to contemporary styles or anything in between. Product specialists are available to help you create your dream space.
                </p>
            </div>
            <div class="flex5">
                <img  src="../assets/image-about-light.jpg">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'Home2',
    data:()=>{
        return{
            index:0,
            menu:false
        }
    },
    computed: {
        currentSlide:function(){
              return this.slideContents[this.index]
            },
        widthChecker:function(){
            if(window.innerWidth > 386){
                console.log(window.innerWidth)
                return 'desktop'
            } else if(window.innerWidth <= 386){
                console.log(window.innerWidth)
                return  'mobile'
            }
        },
        slideContents(){
            return [
                 {
                    picture: require(`../assets/${this.widthChecker}-image-hero-1.jpg`),
                    header:'Discover innovative ways to decorate',
                    content:'We provide unmatched quality, comfort, and style for property owners across the country. Our experts combine form and function in bringing yourj vision to life. Create room in your own style with our collection and make your property a reflection of you and what you love.'
                },
                {
                    picture: require(`../assets/${this.widthChecker}-image-hero-2.jpg`),
                    header:'We are available all across the globe ',
                    content:"With stores all over the world, i'ts easy for you to find furniture for your home or place of business. Locally, we're in most major cities throughout the country. Find the branch nearest you using our store locator. Any questions? Don't hesitate to contact us today."
                },
                {
                    picture: require(`../assets/${this.widthChecker}-image-hero-3.jpg`),
                    header:'Manufactured with the best materials',
                    content:"Our modern furniture provide a high level of quality. Our company has invested in advanced technology to ensure every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office."
                }
            ]
        }
    },
    methods:{
        slideNext(){
            if(this.index <= 2){ 
               return this.index++
              } else {
                return this.index
              }
        },
        slidePrev(){
            if(this.index <= 3 && this.index > 0){
                return this.index --
            } else {
                return this.index
            }
        }
    }
}
</script>

<style scoped>
.hamburgerIcon{
    color:black
}

.container{
    display:inline-flex;
    padding:0px;
    margin:0px;
}
.flex1{
    width:60%;
}

.top-image{
    width:115%
}

.flex2{
    width:40%;
    margin-top:5%;
    margin-left:8%;
    margin-right:0%;
    padding-left:1%;
    padding-right:1%;
    height:41vh
}
.layout{
    display:inline-flex;
    width:100%;
    margin-top:0px;
    padding-top:0px
}

.flex3{
    width:30%;
    margin-top:-5px
}

.flex4{
    width:40%;
    padding-left:4%;
    padding-right:4%
}
.flex5{
    width:30%;
    margin-top:-5px;
}

.navigation{
    position:absolute;
    top:40px;
    z-index:2;
}

.v-list{
    background:transparent !important;
    margin-left:5vh
}

.v-list .v-list-item{
    display:inline-flex;
    flex-direction: column;
    cursor: pointer;
    font-weight: bold;
    font-size:12px
}

.v-list :nth-child(1){
    font-size:22px;
    font-weight: bold;
    margin-left:4vh;
    margin-right:4vh;
}

.slider-header{
    font-size:30px !important;
    font-weight: 700;
    margin-top:9%;
    margin-bottom:9%;
    padding:0px 0px 0px 84px
}

.content-wrap{
    height:28.3%;
    padding: 0px 0px 0px 84px
}

.about-header{
    font-family:"Spartan";
    font-weight: bold;
    font-size:13px;
    letter-spacing: 4px;
    padding-bottom:10px;
    padding-left:20px
}

.about-content{
    padding-left: 20px;
    color: hsl(0, 0%, 63%)
}

span{
    color:hsl(0, 0%, 63%)
}

.btn-wrapper{
    margin-top:6.2%;
    margin-left:-2.4%;
    margin-right:auto;
    display:flex;
    width:155px;
    height:70px;
    background-color: black;
}

.btn-wrapper button{
    margin-left:21%;
    margin-right:15%;
}

.v-btn{
    background-color: black !important;
}

.shop-now{
    display:inline-flex;
    margin-top:15%;
    margin-right:20px;
    cursor:pointer;
    padding: 0px 0px 0px 84px
}

.shop-text{
    font-family:"Spartan";
    font-size: 14px;
    letter-spacing: 12px;
    margin-left:3px;
    color:black
}

.v-list :nth-child(1):hover{
    text-decoration: underline 
}

.v-list :nth-child(2):hover{
    text-decoration: underline 
}

.v-list :nth-child(3):hover{
    text-decoration: underline 
}

.v-list :nth-child(4):hover{
    text-decoration: underline 
}

.v-list :nth-child(5):hover{
    text-decoration: underline 
}

@media only screen and (max-width:390px){
    .container{
        display:block
    }

    .navigation{
        display:none
    }

    .flex1{
        width:100%
    }

    .btn-wrapper{
        position:relative;
        margin-top:-70vh;
        float:right;
        height:70px;
        left:-6%;
        width:130px
    }


    .nav{
        margin-top: 0%;
        height:70px;
        background:linear-gradient(90deg, rgb(143, 141, 141), rgb(204, 202, 202), rgb(143, 141, 141))
    }

    .hamburgerIcon{
        position:absolute;
        z-index:1;
        top:20px;
        left:20px;
        cursor:pointer
    }
    
    .mobileTitle{
        position:absolute;
        z-index:2;
        top:15px;
        left:130px;
        background:transparent;
        font-size:20px;
        font-weight: bold;
        margin-left:4vh;
        margin-right:4vh;
        color:white
    }

    .layout{
        display:block;
        margin-top:-50px
    }

    .flex2{
        width:100%;
        padding-left:0px;
        padding-right:0px
    }

    .flex3{
        width:100%;
        margin-top:-5px
    }

    .flex4{
        width:100%;
        padding-left:8%;
        padding-right:8%
    }

    .flex5{
        width:100%;
        margin-top:13%
    }

    .slider-header{
        margin-top:15%;;
        padding-left:0px;
        padding-right:10%
    }

    .content-wrap{
        padding-left:0px;
        padding-right:15%
    }

    .shop-now{
        padding-left:0px
    }

    .closeButton{
        scale:1.1;
        right:40px;
        top:8%
    }

    .v-list >*{
        width:50px;
        color:black;
        font-size:16px;
        font-weight: bold;
        font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
        margin-top:10%
    }

    .mob-navigation{
        align-content: center;
    }

    .v-list :nth-child(2):hover{
        text-decoration: underline 
    }
}
</style>

