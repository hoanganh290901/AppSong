<template>
  <Page actionBarHidden="true">
   <GridLayout orientation="vertical" width="100%" height="100%" columns="*" rows="*,auto,auto,auto,auto,auto,auto,auto">
     <!-- thiết kế nội dung -->
     <StackLayout col="0" row="0">
       <GridLayout columns="auto,*,auto" rows="auto,*,auto" height="200" class="detail-page"
       backgroundImage="~/assets/images/anhlogin.jpg">
        <!-- nút đảo lại nằm ở cột thứ 0 -->
        <Image src="~/assets/images/back.png" col="0" row="0" height="25" width="25" marginLeft="20" marginTop="10"
        @tap="$navigateBack(App)"/>
        <Label text="Hoanganh3001190575" row="2" colSpan="3" paddingLeft="20" fontWeight="bold" fontSize="20" color="black"/>
       </GridLayout>
       <!-- thiết kế Tai khoan -->
       <Label text="Account" marginTop="10" fontSize="20" paddingLeft="10" color="black"/>
        <!-- dòng 1 -->
       <StackLayout orientation="vertical" row=1 backgroundColor="rgb(170, 245, 241)">
        <Label text="Playlist" class="h1" style="font-weight: bold; font-size: 30px"/>
        </StackLayout>
        <!-- dòng 2 -->
       <StackLayout orientation="vertical" row=2 backgroundColor="rgb(170, 245, 241)">
        <Label text="Video" class="h1" style="font-weight: bold; font-size: 30px"/>
        </StackLayout>
        <!-- dòng 3 -->
        <!-- dòng 4 -->
        <Label text="Offline" row=4 marginTop="10" fontSize="20" paddingLeft="10" color="black"/>
        <!-- dòng 5 -->
        <StackLayout orientation="vertical" row=5 backgroundColor="rgb(170, 245, 241)">
        <Label text="Thư viện nhạc" class="h1" style="font-weight: bold; font-size: 30px"/>
        </StackLayout>
        <!-- dòng 6 -->
        <StackLayout orientation="vertical" row=6 backgroundColor="rgb(170, 245, 241)">
        <Label text="Video" class="h1" style="font-weight: bold; font-size: 30px"/>
        </StackLayout>
        <!-- dòng 7 -->
        <StackLayout orientation="vertical" row=7 backgroundColor="rgb(170, 245, 241)">
        <Label text="Đã tải" class="h1" style="font-weight: bold; font-size: 30px"/>
        </StackLayout>
     </StackLayout>
            <!-- Thiết kế nội dung  -->
    

   </GridLayout>
  </Page>
</template>
<script>
export default {
  data() {
    return {
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