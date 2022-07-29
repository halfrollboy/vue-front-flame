<template>
    <div class="discussion search">
        <div class="searchbar">
            <i class="fa fa-search" aria-hidden="true"></i>
            <input type="text" placeholder="Search...">
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return
    }
}
</script>

<style>
.discussions .search {
    display: flex;
    align-items: center;
    justify-content: center;
    color: #E0E0E0;
}

.discussions .search .searchbar {
    height: 40px;
    background-color: #FFF;
    width: 70%;
    padding: 0 20px;
    border-radius: 50px;
    border: 1px solid #EEEEEE;
    display: flex;
    align-items: center;
    cursor: pointer;
}

.discussions .search .searchbar input {
    margin-left: 15px;
    height: 38px;
    width: 100%;
    border: none;
    font-family: 'Montserrat', sans-serif;
}

.discussions .search .searchbar *::-webkit-input-placeholder {
    color: #E0E0E0;
}

.discussions .search .searchbar input *:-moz-placeholder {
    color: #E0E0E0;
}

.discussions .search .searchbar input *::-moz-placeholder {
    color: #E0E0E0;
}

.discussions .search .searchbar input *:-ms-input-placeholder {
    color: #E0E0E0;
}

.discussion .search {
    position: fixed;
}
</style>