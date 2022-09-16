<template>
    <div id="align">
        <b-jumbotron id="fundo">
            <h1 class="text-uppercase">To - Do List</h1>
            <p>feito por <a href="https://github.com/cruxsacrasitmihilux">Ygor Samuel</a></p>
        </b-jumbotron>
    </div>
</template>

<script>
import ToastMixin from "@/mixins/toastMixin.js";

export default {
  name: "Home",
}
</script>

<style>
#fundo{
    background-color: #000000;
}

#fundo h1{
    color: #FFC905;
    font-weight: 700 !important;
    font-size: 11rem !important;
}

#fundo p{
    color: #FFC905;
    font-weight: 400 !important;
    font-size: 20px !important;
}

#fundo a{
    font-family: 'Dancing Script', cursive;
    text-decoration: none;
    color: #FEEDE1;
    font-weight: 600 !important;
    font-size: 24px;
}

#align{
    height: calc(100vh - 56px);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
}

@media only screen and (max-width: 768px) {
    #fundo h1{
    color: #FFC905;
    font-weight: 700 !important;
    font-size: 5rem !important;
}
}

</style>

