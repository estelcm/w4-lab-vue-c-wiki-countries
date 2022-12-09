<template>
    <div class="col-7">
        <img :src="'https://www.geonames.org/flags/x/' + showCountry.alpha2Code.toLowerCase() + '.gif'"
         alt="country flag" style="width: 300px" />
        <h1>{{showCountry.name.common}}</h1>
        <table class="table">
            <thead></thead>
            <tbody>
                <tr>
                    <td style="width: 30%">Capital</td>
                    <td>{{showCountry.capital[0]}}</td>
                </tr>
                <tr>
                    <td>Area</td>
                    <td>
                       {{showCountry.area}}  km <sup>2</sup>
                    </td>
                </tr>
                <tr>
                    <td>Borders</td>
                    <td>
                        <ul v-for="(country,index) in showCountry.borders" :key="index">
                            <li>
                            <routerLink :to="`/${showCountry.alpha3Code}`">{{country}}
                            </routerLink>
                            </li> 
                            <!-- <li><a href="/BEL"></a></li>
                            <li><a href="/DEU"></a></li>
                            <li><a href="/ITA"></a></li>
                            <li><a href="/MCO"></a></li>
                            <li><a href="/ESP"></a></li>
                            <li><a href="/CHE"></a></li> -->
                        </ul>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    import countries from "../../public/countries.json";
    
export default {
    data (){
        return{
        countries:countries,
    }

   },
   computed:{

    showCountry(){
const countryId= this.$route.params.alpha3Code;
return this.countries.find(function(country){
    if(country.alpha3Code === countryId){
        return true;
    }
    else {
        return false;
    }
    });
    }
}
    
    // // showCountry() {
    //    return this.countries.find((project)=>
    //    (country ===this.$route.params.alpha3Code)
    //    );
    // }
  } ;

    // mounted() {
    //     // NO se tiene que hacer en mounted
    //     console.log(this.$route.params)
    // }

 


</script>