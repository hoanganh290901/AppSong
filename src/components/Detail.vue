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
        <Label text="Make a sponsor" col="2" row="0" fontSize="12" color="red"/>
       </GridLayout>
       <!-- thiết kế Top Song -->
       <Label text="Mới Phát Hành" marginTop="10" fontSize="20" paddingLeft="10" color="black"/>
       <!-- Thiết kế nội dung -->
       <ListView for="item in music " class="list-group" @itemTap="onItemTap">
         <v-template>
           <GridLayout columns="auto,*,auto" rows="auto" class="list-group-item">
             <!-- thiết kế image nam cot 0 -->
             <Image col="0" row="0" :src="item.imageUrl" height="75" width="75"/>
             <!-- thiêt kê tên bai hat, ca sĩ, nanm cột 1 -->
             <StackLayout col="1" row="0" marginLeft="15">
               <Label :text="item.title" marginTop="5" paddingRight="5" color="#111111"/>
               <Label :text="item.artist" marginTop="5" paddingRight="5" color="#111111"/>
               <Label :text="item.year" marginTop="5" paddingRight="5" color="#111111"/>
             </StackLayout>
             <!-- thiết kế biểu tượng icon  -->
              <Label col="2" row="0" horizontalAlignment="right" marginRight="5"  width="50" height="20"
                  class="fas" :text="'fa-headphones'|fonticon" color="Blue"/>
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
      listViewData: [
      {
          imageUrl: "~/assets/images/muonroi.jpg",
          title: "Muộn Rồi Mà Sao Còn",
          artist: "Sơn Tùng MTP",
          webSrc: 'https://www.nhaccuatui.com/bai-hat/muon-roi-ma-sao-con-son-tung-m-tp.6nAqBAZ3nxuV.html'
      },
      {
          imageUrl: "~/assets/images/tractronho.jpg",
          title: "Trắc Trở",
          artist: "X2X",
          webSrc: 'https://www.nhaccuatui.com/bai-hat/trac-tro-x2x.euuuwjUAqLcX.html'
      },
      {
          imageUrl: "~/assets/images/2phut.jpg",
          title: "2 Phút Hơn",
          artist: "Pháo",
          webSrc: 'https://www.youtube.com/watch?v=yoZy2E17-50&list=RDGMEMYH9CUrFO7CfLJpaD7UR85w&start_radio=1&rv=wSxijea-o_M'
      },
      {
          imageUrl: "~/assets/images/chieuthu.jpg",
          title: "Chiều Thu Họa Bóng Nàng",
          artist: "DatKaa",
          webSrc: 'https://www.youtube.com/watch?v=PlVlWl8kKmg'
      },
      {
          imageUrl: "~/assets/images/tuongquan.jpg",
          title: "Tướng Quân",
          artist: "Nhật Phong",
          webSrc: 'https://www.youtube.com/watch?v=wSxijea-o_M&list=RDGMEMYH9CUrFO7CfLJpaD7UR85wVMwSxijea-o_M&start_radio=1'
      },
      {
          imageUrl: "~/assets/images/cogiangtinh.jpg",
          title: "Cố Giang Tình",
          artist: "X2X",
          webSrc: 'https://www.nhaccuatui.com/bai-hat/co-giang-tinh-orinn-remix-x2x.BCYrrDe9HQf5.html'
      },        
			{
					title: "Kiếp Thứ II",
					artist: "Linh Cáo",
					year: "2020",
					imageUrl: "~/assets/images/linhcao.jpg",
					webSrc: 'https://www.youtube.com/watch?v=ADuxk-q745I'
			},
			{
					title: "Yêu Một NGười Sao Buồn Đến Thế",
					artist: "Noo Phước Thịnh",
					year: "2020",
					imageUrl: "~/assets/images/noophuocthinh.jpg",
					webSrc: 'https://www.nhaccuatui.com/mh/auto/OYEw8BeT2E2P'
			},
			{
					title: "Đôi Mình Bên Nhau",
					artist: "Linh Cáo",
					year: "2019",
					imageUrl: "~/assets/images/doiminhbennhau.jpg",
					webSrc: 'https://www.nhaccuatui.com/vh/auto/khkDe0WqpBJpf'
			},
			{
					title: "Em Không Sai Chúng Ta Sai",
					artist: "Erik",
					year: "2020",
					imageUrl: "~/assets/images/erik.jpg",
					webSrc: 'https://www.nhaccuatui.com/vh/auto/8NX7D7ItvnhuQ'
			},
			{
					title: "Đúng Cũng Thành Sai",
					artist: "Mỹ Tâm",
					year: "2020",
					imageUrl: "~/assets/images/mytam.jpg",
					webSrc: 'https://youtu.be/5_ozB0ImkYA'
			},
			{
					title: "Tình Nào Không Như Tình Đầu",
					artist: "Trung Quân Idol",
					year: "202020",
					imageUrl: "~/assets/images/trungquan.jpg",
					webSrc: 'https://www.nhaccuatui.com/mh/auto/yYUyCwMsNhmR'
			},
	  ],
    music:[]
    }
  },
  mounted() {
    this.doSort();

    this.music = this.listViewData;
  },
  methods: {
    doSort() {
      this.listViewData.sort((a, b) => (a.title > b.title ? 1 : -1));
    },
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