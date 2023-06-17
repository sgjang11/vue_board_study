<template>
    <div>
        <h2>사용자 게시판</h2>
        <div class="container" v-for="(value,i) in data" :key="i" @click="detail(i)">
            <div class="f_wrap">
                <div class="title">
                    {{value.title}}
                </div>
                <div class="name">
                    {{value.writer}}
                </div>
            </div>
            <div class="content">
                {{value.content}}
            </div>
        </div>
        <button @click="write">글쓰기</button>
    </div>
</template>
<script>
import data from '@/data'
export default {
    data(){
        return {
            data : data
        }
    },
    methods: {
        write(){
            this.$router.push({
                path: 'create'
            })
        },
        detail(i){
            this.$router.push({
                name:'Detail',
                params:{
                    contentId:i
                }
            })
        }
    },
}
</script>
<style>

</style>