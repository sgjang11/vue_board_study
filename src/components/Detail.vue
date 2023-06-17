<template>
    <div>
        <h2>상세페이지</h2>
        <div class="container">
            <div class="f_wrap">
                <div class="title">{{data.title}}</div>
                <div class="writer">{{data.writer}}</div>
            </div>
            <div class="content">
                {{data.content}}<br><br>
                <img :src="data.image">
            </div>
        </div>
        <button @click="updateData">수정</button>
        <button @click="delData">삭제</button>
        <button @click="goHome">HOME</button>
    </div>
</template>
<script>
import data from "@/data";
export default {
    name: 'Detail',
    data() {
        const index = this.$route.params.contentId
        return {
            data: data[index],
            index: index
        };
    },
    methods: {
        delData(){
            data.splice(this.index, 1)
            this.$router.push({
                path: '/'
            })
        },
        updateData(){
            this.$router.push({
                name: 'Create',
                params: {
                    contentId:this.index
                }
            })
        },
        goHome(){
            this.$router.push({
                path: '/'
            })
        }
    },
}
</script>
<style>
    
</style>