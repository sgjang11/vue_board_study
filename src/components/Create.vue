<template>
    <div>
        <h2>게시판 {{index !== undefined ? '수정하기':'글쓰기'}}</h2>
        <div class="container">
            <input type="text" v-model="writer" placeholder="글쓴이">
            <input type="text" v-model="title" placeholder="제목">
            <textarea v-model="content" cols="30" rows="10" placeholder="제목">
            </textarea>
            <input type="text" v-model="image" placeholder="이미지">
            <div>
                <img :src="image">
            </div>
        </div>
        <button @click="index !== undefined ? update() : write()">{{index !== undefined ? '수정하기':'글쓰기'}}</button>
    </div>
</template>
<script>
import data from '@/data'
export default {
    name : 'Create',
    data() {
        const index = this.$route.params.contentId
        return {
            data: data,
            index: index,
            writer: index !== undefined? data[index].writer:'',
            title: index !== undefined? data[index].title:'',
            content: index !== undefined? data[index].content:'',
            image: index !== undefined? data[index].image:''
        };
    },
    methods: {
        write(){
            this.data.push({
                writer:this.writer,
                title:this.title,
                content:this.content,
                image:this.image
            })
            this.$router.push({
                path: '/'
            })
        },
        update(){
            data[this.index].writer = this.writer
            data[this.index].title = this.title
            data[this.index].content = this.content
            data[this.index].image = this.image
            this.$router.push({
                path: '/'
            })
        }
    },
}
</script>
<style>
</style>