<template>
    <div id="app">
        {{ msg }}
        <button id="btn">시작</button>
        <p id="pEl"></p>
    </div>
</template>

<script>
export default {
    data () {
        return {
            msg: 'Hello Vue.js!'
        }
    },
    created() {
        $('#btn').click(function() {
            $('#pEl').text('jQuery');
        });
    }
}
</script>

<style>
</style>