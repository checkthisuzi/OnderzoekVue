<template>
     <div class="task">
        <h3 class="my-4 text-center text-lg-left">Family</h3>
        <div class="row text-center text-lg-left">
            <div class="col-lg-3 col-md-4 col-xs-6  bg-dark" v-for="item in familyList" >
                {{item.name}}
            </div>
        </div>
     </div>
</template>

<script>
export default {
    name: 'Family',
     data: function() {
         return  {
           familyList: []
         }
    },
    created: function () {
        this.fetchData();
    },
    methods: {
        fetchData: function () {
            this.familyId = JSON.parse(localStorage.getItem('dbUser')).family_id;
            if(this.familyId != 0){
                this.$http.get('https://stefanbode.nl/api/user/read_by_family.php?family_id='+this.familyId).then(response => {
                    this.familyList = response.data.records;
                 })
             } else {
                this.familyList = [];
             }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>