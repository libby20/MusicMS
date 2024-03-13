<template>
    <div class="content-list">
        <ul class="section-content">
            <li class="content-item" v-for="(item,index) in contentList" :key="index">
                <div class="kuo" @click="goAlbum(item,item.type)">
                    <img class="item-img" :src="attachImageUrl(item.pic)">
                    <div class="mask">
                        <svg class="icon">
                            <use xlink:href="#icon-bofang"></use>
                        </svg>
                    </div>
                </div>
                <p class="item-name">{{item.name||item.title}}</p>
            </li>
        </ul>
    </div>
</template>
<script>
import {mixin} from '../mixins';
export default {
    name: 'content-list',
    mixins: [mixin],
    props: ['contentList'],
    methods: {
        goAlbum(item,type){
            this.$store.commit("setTempList",item);
            console.log('---------TYPE----->>',type)
            if(type==1){                   //歌手
                this.$router.push({path:`singer-album/${item.id}`});
            }else if(type==0){                      //歌单
                this.$router.push({path:`song-list-album/${item.id}`});
            }else{                        //歌曲
              this.$router.push({path:`song-album/${item.id}`});
            }
        }
    }
}
</script>
<style lang="scss" scoped>
@import '../assets/css/content-list.scss';
</style>
