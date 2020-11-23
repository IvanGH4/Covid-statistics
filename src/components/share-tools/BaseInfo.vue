<template>
    <div class="wrapper">
        <nav class="navbar navbar-expand-lg bg-dark text-light">
            <h2>Global Covid Statistics</h2>
        </nav>
        <div class="container my-3">
            <div class="row">
                <div class="col-md-6 bg-success rounded-pill text-light p-3 text-center mt-3">
                    <h3>Cases today</h3>
                    <hr>
                    <h2>{{this.covid[0].todayCases}} today cases</h2>
                </div>
                <div class="col-md-6 bg-warning rounded-pill text-light p-3 text-center mt-3">
                    <h3>Total cases</h3>
                    <hr>
                    <h2>{{this.covid[0].cases}}</h2>
                </div>
            </div>

            <div class="row my-3">
                <div class="col-md-6 bg-dark rounded-pill text-light p-3 text-center mt-3">
                    <h3>Deaths today</h3>
                    <hr>
                    <h2>{{this.covid[0].todayDeaths}}</h2>
                </div>
                <div class="col-md-6 bg-dark rounded-pill text-light p-3 text-center mt-3">
                    <h3>Total deaths</h3>
                    <hr>
                    <h2>{{this.covid[0].deaths}}</h2>
                </div>
            </div>

            <div class="row d-flex justify-content-center my-3">
                <div class="col-lg-8 text-center rounded-pill bg-danger text-light mt-3">
                    <h3>Affected countries</h3>
                    <hr>
                    <p>{{this.covid[0].affectedCountries}}</p>
                </div>
            </div>
        </div>
        <!-- <p>{{this.covid[0].active}} total cases</p>
        <p>{{this.covid[0].todayCases}} today cases</p> -->
    </div>
</template>

<script>
export default {
    name: 'BaseInfo',
    data(){
        return{
            covid: []
        }
    },
    mounted() {
        const url = 'https://disease.sh/v3/covid-19/all';
        fetch(url)
        .then(response => response.json())
        .then(data => {
            this.covid.push(data);
            console.log(this.covid);
        })
        .catch((err)=>console.log(err));
        
    }

}
</script>