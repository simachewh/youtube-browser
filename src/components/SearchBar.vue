<template>
    <div>
        <input type="text" @input="onSearchInput"/>
    </div>
</template>

<script>
export default {
    name : "SearchBar",
    methods : {
        onSearchInput : function( event ) {
            this.$emit( "searchTermChange", event.target.value );
        }
    }
}
</script>

<style>

</style>
