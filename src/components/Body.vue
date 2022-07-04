<script>
import College from './College.vue'

export default{
    components:{
        College
    },
    data(){
        return {
            myArray: '',
            inputData:'',
        }
    },
    methods: {
        process(){
            var link = this.inputData.replace(/\s/g, '+') 
            var url = 'http://universities.hipolabs.com/search?country=' + link
            console.log(url)
            /*fetch(url)
            .then(response => response.text())
            .then(data =>{ 
                    this.myArray = JSON.parse(data)      
            })*/ /*This is the alternative fetch method to http request */
            
            const Http = new XMLHttpRequest();
            Http.open("GET", url);
            Http.send();

            Http.onreadystatechange = (e) => {
                console.log(Http.responseText)
                this.myArray = JSON.parse(Http.responseText)
            }
        }
    }   
}

</script>

<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <h1>Universities List</h1>
                <p class="mb-0">Enter Country Name :</p>
                <input v-model="inputData"  placeholder="e.g United States"/>
                <br/>
                <br/>
                <button @click="process" class="btn btn-danger mb-2">Search</button>
            </div>
            <div class="row">
                 <div class="col-lg-8 offset-lg-2 col-md-8 offset-md-2">
                    <div class="row">
                    <College v-for="school in myArray" :collegeStateProvince="school['state-province']" 
                    :collegeWebpages="school.web_pages[0]" :collegeCountry="school.country"
                    :collegeDomain="school.domains[0]" :collegeAlphaTwoCode="school.alpha_two_code"
                    :collegeName="school.name" :collegeIndex="myArray.indexOf(school) + 1"/>
                    </div>
                 </div>
            </div>
               
             
        </div>
    </div>
</template>