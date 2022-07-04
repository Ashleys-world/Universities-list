<script>
export default{
    props:{
        collegeName : String ,
        collegeWebpages : '',
        collegeCountry : String,
        collegeDomain : '' ,
        collegeAlphaTwoCode : String,
        collegeStateProvince : String,
        collegeIndex:''
    }
}
</script>

<template>
<div class="col-lg-6 col-md-6">
    <div class="card border-danger mx-2 my-2">
        <div class="card-header card-title">
            <h5>University : {{collegeIndex}}</h5>
        </div>
        <div class="card-body ">
            <h5 class="">{{collegeName}}</h5>
            <p class="my-2">State/Province : {{collegeStateProvince}}</p>
            <p class="my-2">Domain : {{collegeDomain}}</p>
            <p class="my-2">Webpages : {{collegeWebpages}}</p>
            <p class="my-2">Alpha Two Code : {{collegeAlphaTwoCode}}</p>
            <p class="my-2">Country : {{collegeCountry}}</p>
        </div>
    </div>
</div>

</template>