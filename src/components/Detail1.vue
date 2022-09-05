<template>
  <Page actionBarHidden="true">
   <GridLayout orientation="vertical" width="100%" height="100%" columns="*" rows="*,auto">
     <!-- thiết kế nội dung -->
     <StackLayout col="0" row="0">
       <GridLayout columns="auto,*,auto" rows="auto,*,auto" height="200" class="detail-page"
       backgroundImage="~/assets/images/doiminhbennhau.jpg">
        <!-- nút đảo lại nằm ở cột thứ 0 -->
        <Image src="~/assets/images/back.png" col="0" row="0" height="25" width="25" marginLeft="20" marginTop="10"
        @tap="$navigateBack(App)"/>
       </GridLayout>
       <!-- thiết kế Top Song -->
       <Label text="Allbum Hot" marginTop="10" fontSize="20" paddingLeft="10" color="black"/>
       <!-- Thiết kế nội dung -->
       <ListView for="item in listViewDataAlbum " class="list-group" @itemTap="onItemTap">
         <v-template>
           <GridLayout columns="auto,*,auto" rows="auto" class="list-group-item">
             <!-- thiết kế image nam cot 0 -->
             <Image col="0" row="0" :src="item.imageUrl" height="75" width="75"/>
             <!-- thiêt kê tên bai hat, ca sĩ, nanm cột 1 -->
             <StackLayout col="1" row="0" marginLeft="15">
               <Label :text="item.title" marginTop="5" paddingRight="5" color="#111111"/>
               <Label :text="item.artist" marginTop="5" paddingRight="5" color="#111111"/>
             </StackLayout>
           </GridLayout>
         </v-template>
       </ListView>
     </StackLayout>
     <!-- thiết kế button -->
   </GridLayout>
  </Page>
</template>
<script>
  import SongModal from './SongModal'
export default {
  data() {
    return {
      listViewDataAlbum : [
        {
          title: "Anh Mệt Rồi",
          artist: "Anh Quân Idol",
          imageUrl: "~/assets/images/anhmetroi.jpg",
        },
        {
          title: "Ai Mang Cô Đơn Đi",
          artist: "K-ICM, ACM",
          imageUrl: "~/assets/images/K_ICM.jpg",
        },
        {
          title: "Hoa Hải Đường",
          artist: "Jack",
          imageUrl: "~/assets/images/jack.jpg",
        },
      ],
    }
  },
  methods: {
    onItemTap(event)
    {
      this.$showModal(SongModal,{
        props:{
          webSrc:event.item.webSrc
        }
      })
    }
  },
}
</script>
<style>
.detail-page{
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>