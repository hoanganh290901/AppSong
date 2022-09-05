
<template>
  <Page loaded="pageLoaded" class="page">
    <ActionBar>
      <StackLayout
        orientation="horizontal"
        width="100%"
        height="100%"
        backgroundColor="#44557f"
      >
        <TextField backgroundColor="white" paddingLeft="20" boderRadius="20" v-model="search"  width="80%" 
        height="40" fontSize="14" hint="Search..."/>
        <Image src="~/assets/images/search.png" height="40" width="40" marginLeft="10"
        />
      </StackLayout>
    </ActionBar>
    <BottomNavigation >
        <TabStrip >
            <TabStripItem >
                  <Label height="50" width="50" class="fas" :text="'fa-home'|fonticon"/>
            </TabStripItem>
            <TabStripItem>
                <Label height="50" width="50" class="fas" :text="'fa-music'|fonticon"/>
            </TabStripItem>
            <TabStripItem>
                <Label height="50" width="50" class="fas" :text="'fa-chart-bar'|fonticon"/>
            </TabStripItem>
            <TabStripItem>
                <Label height="50" width="50" class="fas" :text="'fa-user'|fonticon"/>
            </TabStripItem>
        </TabStrip>

        <TabContentItem>
          <!-- home -->
            <StackLayout>
          <!-- Thiết kế layout 2 nội dung chính -->
          <!-- Nội dung thứ 1 là chứa bố cục của bài nhạc, nội dung thứ 2 chứa button -->
              <GridLayout
                orientation="vertical"
                width="100%"
                height="100%"
                columns="*"
                rows="*,auto"
              >
                <!-- bố cục cho dòng 0 là các bài nhạc -->
                <StackLayout col="0" row="0" backgroundColor="#f8f8f8">
                  <!-- thiết kế chữ Song MP3 -->
                  <StackLayout
                    backgroundColor="#F6CEE3"
                    paddingBottom="15"
                    marginTop="-10"
                  >
                    <Label
                      text="Song MP3"
                      fontWeight="bold"
                      color="#fffff"
                      padding="15"
                      fontSize="24"
                    />
                  </StackLayout>
                  <!-- thiết kế Nật ký khu cách ly -->
                  <StackLayout
                    paddingLeft="20"
                    paddingRight="20"
                    paddingTop="20"
                    paddingBottom="5"
                    marginTop="-20"
                    backgroundImage="~/assets/images/tractro.jpg"
                    borderRadius="5"
                    height="180"
                    width="90%"
                    stretch="aspectFit"
                    class="album-image"
                  >
                    <GridLayout columns="*" rows="auto,auto" height="100%" color="white">
                      <Label
                        text="Bài Hát Việt Nam Hay Nhất 2021"
                        row="0"
                        col="0"
                        fontWeight="bold"
                        fontSize="18"
                      />
                      <Label
                        text="by X2X"
                        row="1"
                        col="0"
                        fontWeight="bold"
                        fontSize="16"
                      />
                    </GridLayout>
                  </StackLayout>
                  <!-- thiết kế Mới phát hành -->
                  <!-- từ tiêu đề mới phát hành đến top song kéo lên xuống đc -->
                  <ScrollView orientation="vertical">
                    <!-- thiết kế Mới phát hàng và View All -->
                    <StackLayout>
                      <GridLayout columns="auto,*,auto" rows="auto">
                        <Label
                          text="Mới Phát Hành"
                          col="0"
                          row="0"
                          fontWeight="bold"
                          fontSize="20"
                          paddingLeft="10"
                          color="#000000"
                          @tap="showDetail()"
                        />
                        <Label
                          :text="'View All :'+ views"
                          col="2"
                          row="0"
                          fontWeight="bold"
                          fontSize="14"
                          marginRight="20"
                          color="#8d8d8d"
                        />
                      </GridLayout>
                      <!-- thiết kế nội dung của mới phát hành -->
                      <ScrollView orientation="horizontal">
                        <StackLayout orientation="horizontal">
                          <!-- thiết kế hình cho những bài nhạc, lấy ra damh sach -->
                          <StackLayout
                            margin="10"
                            v-for="item in listViewDataNew"
                            :key="item.title"
                          >
                            <GridLayout
                              class="album-image"
                              height="110"
                              width="125"
                              borderRadius="5"
                              :backgroundImage="item.imageUrl"
                            >
                              <Label
                                horizontalAlignmnet="right"
                                marginRight="5"
                                marginTop="80"
                                width="50"
                                height="20"
                                class="fa btn-rounded-sm"
                                color="red"
                                >{{ "fa-star" | fonticon }}</Label
                              >
                            </GridLayout>
                            <Label
                              :text="item.title"
                              fontSize="14"
                              fontWeight="bold"
                              color="#000000"
                            />
                            <Label
                              :text="item.artist"
                              fontSize="12"
                              fontWeight="bold"
                              color="#999999"
                            />
                          </StackLayout>
                        </StackLayout>
                      </ScrollView>
                      <!-- end moi phat hanh -->
                      <!-- album hot -->
                      <GridLayout columns="auto,*,auto" rows="auto">
                        <Label
                          text="Album Hot"
                          col="0"
                          row="0"
                          fontWeight="bold"
                          fontSize="20"
                          paddingLeft="10"
                          color="#000000"
                          @tap="showDetail1()"
                        />
                        <Label
                          :text="'View All :'+ views1"
                          col="2"
                          row="0"
                          fontWeight="bold"
                          fontSize="14"
                          marginRight="20"
                          color="#8d8d8d"
                        />
                      </GridLayout>
                      <!-- thiết kế nooij dung của album -->
                      <ScrollView orientation="horizontal">
                        <StackLayout orientation="horizontal">
                          <!-- thiết kế hình cho những bài nhạc, lấy ra damh sach -->
                          <StackLayout
                            margin="10"
                            height="130"
                            width="125"
                            v-for="item in listViewDataAlbum"
                            :key="item.title"
                            borderRadius="5"
                          >
                            <!-- thiết kế hình nhỏ nằm gốc trên bên phải -->
                            <Image
                              :src="item.imageUrl"
                              width="20"
                              height="20"
                              horizontalAlignment="right"
                              marginRight="5"
                            />
                            <!-- thiết kế hình to ở giữa tên ca sĩ và bài hát -->
                            <StackLayout
                              horizontalAlignment="center"
                              verticalAlignment="center"
                            >
                              <!-- hình lớn -->
                              <Image
                                height="50"
                                width="50"
                                :src="item.imageUrl"
                                borderRadius="50"
                              />
                              <!-- tên bài hát -->
                              <Label
                                :text="item.title"
                                fontSize="14"
                                fontWeight="bold"
                                color="#000000"
                              />
                              <!-- tên ca sĩ -->
                              <Label
                                :text="item.artist"
                                fontSize="12"
                                fontWeight="bold"
                                color="#999999"
                              />
                            </StackLayout>
                          </StackLayout>
                        </StackLayout>
                      </ScrollView>
                      <!-- end album hot -->
                      <!-- top song -->
                      <GridLayout columns="auto,*,auto" rows="auto">
                        <Label
                          text="Top Song"
                          col="0"
                          row="0"
                          fontWeight="bold"
                          fontSize="20"
                          paddingLeft="10"
                          color="#000000"
                          @tap="showDetail2()"
                        />
                        <Label
                          :text="'View All :'+ views2"
                          col="2"
                          row="0"
                          fontWeight="bold"
                          fontSize="14"
                          marginRight="20"
                          color="#8d8d8d"
                        />
                      </GridLayout>
                      <!-- thiết kế nội dung của Topsong -->
                      <ScrollView orientation="horizontal">
                        <StackLayout orientation="horizontal">
                          <!-- thiết kế hình cho những ca sĩ và tên ca sĩ -->
                          <StackLayout
                            margin="10"
                            v-for="item in listViewDataTopSong"
                            :key="item.title"
                          >
                            <GridLayout
                              class="album-image"
                              height="110"
                              width="125"
                              borderRadius="5"
                              :backgroundImage="item.imageUrl"
                            >
                              <Label
                                horizontalAlignmnet="right"
                                marginRight="5"
                                marginTop="80"
                                width="50"
                                height="20"
                                class="fa btn-rounded-sm"
                                color="red"
                                >{{ "fa-star" | fonticon }}</Label
                              >
                            </GridLayout>
                            <Label
                              :text="item.album"
                              fontSize="14"
                              fontWeight="bold"
                              color="#000000"
                            />
                          </StackLayout>
                        </StackLayout>
                      </ScrollView>
                      <!-- end top song -->
                    </StackLayout>
                  </ScrollView>
                </StackLayout>   
              </GridLayout>
            </StackLayout>
        </TabContentItem>

        <TabContentItem>
          <!-- Music -->
            <StackLayout>
              <ListView for="obj in filterName"  >
                <v-template>
                    <FlexboxLayout flexDirection="row">
                        <StackLayout orientation="vertical">
                            <!--Tiêu đề-->
                            <Label :text="obj.header" color="#FF0000" fontSize="20" backgroundColor="lightgray"/>
                            <!--GridLayout như là 1 table có dòng và cột-->
                            <GridLayout  :key="item.name" v-for="item in obj.items" columns="auto,*,auto,auto" rows="auto,25"
                                        verticalAlignment="top" >
                                <!-- thiết kế image nam cot 0 -->
                              <Image col="0" row="0" :src="item.imgsrc" height="75" width="75"/>
                              <!-- thiêt kê tên bai hat, ca sĩ, nanm cột 1 -->
                              <StackLayout col="1" row="0" marginLeft="15">
                                <Label :text="item.name" marginTop="5" paddingRight="5" color="#111111"/>
                                <Label :text="item.artist" marginTop="5" paddingRight="5" color="#111111"/>
                              </StackLayout>
                                <Button text="Play"   col="3" @tap="onSong(item.webSrc)"/>
                            </GridLayout>
                        </StackLayout>
                    </FlexboxLayout>
                </v-template>
              </ListView>
            </StackLayout>
        </TabContentItem>

        <TabContentItem>
          <!-- bản xếp hạng -->
            <StackLayout>
                <GridLayout orientation="vertical" width="100%" height="100%" columns="*" rows="*,auto">
                  <!-- thiết kế nội dung -->
                  <StackLayout col="0" row="0">
                    <GridLayout columns="auto,*,auto" rows="auto,*,auto" height="200" class="detail-page"
                    backgroundImage="~/assets/images/muonroimasaocon.jpg">
                      <!-- nút đảo lại nằm ở cột thứ 0 -->
                      <Label text="Sơn Tùng MTP" row="2" colSpan="3" paddingLeft="20" fontWeight="bold" fontSize="30" color="#FFFFF"/>
                    </GridLayout>
                    <!-- thiết kế Top Song -->
                    <Label text="Bảng Xếp Hạng" marginTop="10" fontSize="20" paddingLeft="10" color="black"/>
                    <!-- Thiết kế nội dung -->
                    <ListView for="item in listDataBXH " class="list-group" @itemTap="onItemTap">
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
                        </GridLayout>
                      </v-template>
                    </ListView>
                  </StackLayout>
                  <!-- thiết kế button -->
                </GridLayout>
            </StackLayout>
        </TabContentItem>
        <TabContentItem>
          <!-- tài khoản -->
            <StackLayout>
                <FlexboxLayout 
                        marginTop="300"
                        flexDirection="column"
                        alignItems="center"
                        >
                            <Button 
                            text="Đăng Nhập" 
                            width="150" height="50"
                            color="#ffffff" fontSize="18"
                            background="#56c596"
                            @tap="showLogin"
                            />
                            <Button 
                            text="Đăng Kí" 
                            width="150" height="50"
                            color="#ffffff" fontSize="18"
                            background="#7be495"
                            @tap="showSign"
                            />
                    </FlexboxLayout>
            </StackLayout>
        </TabContentItem>
    </BottomNavigation>
</Page>
</template>


<script >
import Detail from "./Detail";
import Detail1 from "./Detail1";
import Detail2 from "./Detail2";
import SongModal from './SongModal'
import Login from './Login.vue'
import Sign from './Sign'
export default {
  data() {
    return {
      listViewDataNew: [
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
            webSrc: 'https://www.nhaccuatui.com/bai-hat/muon-roi-ma-sao-con-son-tung-m-tp.6nAqBAZ3nxuV.html'
        },
        {
          title: "Đôi Mình Bên Nhau",
          artist: "Bạc Cẩm Diễm My",
          imageUrl: "~/assets/images/baccamdiemmy.jpg",
        },
      ],
      listViewDataTopSong: [
        {
          album: "Sơn Tùng",
          imageUrl: "~/assets/images/sontung.jpg",
        },
        {
          album: "Trịnh Thăng Bình",
          imageUrl: "~/assets/images/trinhthangbinh.jpg",
        },
        {
          album: "X2X",
          imageUrl: "~/assets/images/x2x.jpg",
        },
        {
          album: "Mr Siro",
          imageUrl: "~/assets/images/mrsiro.jpg",
        },
        {
          album: "Hương Tràm",
          imageUrl: "~/assets/images/huongtram.jpg",
        },
      ],
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
      listDataBXH: [
			{
					title: "Muộn Rồi Mà Sao Còn",
					artist: "Sơn Tùng MTP",
					year: "2021",
					imageUrl: "~/assets/images/muonroi.jpg",
					webSrc: 'https://www.nhaccuatui.com/bai-hat/muon-roi-ma-sao-con-son-tung-m-tp.6nAqBAZ3nxuV.html'
			},
			{
					title: "Trắc Trở",
					artist: "X2X",
					year: "2021",
					imageUrl: "~/assets/images/tractronho.jpg",
					webSrc: 'https://www.nhaccuatui.com/bai-hat/trac-tro-x2x.euuuwjUAqLcX.html'
			},
      {
          imageUrl: "~/assets/images/2phut.jpg",
          title: "2 Phút Hơn",
          artist: "Pháo",
          year: "2021",
          webSrc: 'https://www.youtube.com/watch?v=yoZy2E17-50&list=RDGMEMYH9CUrFO7CfLJpaD7UR85w&start_radio=1&rv=wSxijea-o_M'
      },
      {
          imageUrl: "~/assets/images/chieuthu.jpg",
          title: "Chiều Thu Họa Bóng Nàng",
          artist: "DatKaa",
          year: "2021",
          webSrc: 'https://www.youtube.com/watch?v=PlVlWl8kKmg'
      },
      {
          imageUrl: "~/assets/images/tuongquan.jpg",
          title: "Tướng Quân",
          artist: "Nhật Phong",
          year: "2021",
          webSrc: 'https://www.youtube.com/watch?v=wSxijea-o_M&list=RDGMEMYH9CUrFO7CfLJpaD7UR85wVMwSxijea-o_M&start_radio=1'
      },
      {
          imageUrl: "~/assets/images/cogiangtinh.jpg",
          title: "Cố Giang Tình",
          artist: "X2X",
          year: "2021",
          webSrc: 'https://www.nhaccuatui.com/bai-hat/co-giang-tinh-orinn-remix-x2x.BCYrrDe9HQf5.html'
      },
			{
					title: "Đôi Mình Bên Nhau",
					artist: "Linh Cáo",
					year: "2021",
					imageUrl: "~/assets/images/doiminhbennhau.jpg",
					webSrc: 'https://www.nhaccuatui.com/vh/auto/khkDe0WqpBJpf'
			},
			{
					title: "Em Không Sai Chúng Ta Sai",
					artist: "Erik",
					year: "2021",
					imageUrl: "~/assets/images/erik.jpg",
					webSrc: 'https://www.nhaccuatui.com/vh/auto/8NX7D7ItvnhuQ'
			},
			{
					title: "Đúng Cũng Thành Sai",
					artist: "Mỹ Tâm",
					year: "2021",
					imageUrl: "~/assets/images/mytam.jpg",
					webSrc: 'https://youtu.be/5_ozB0ImkYA'
			},
			{
					title: "Tình Nào Không Như Tình Đầu",
					artist: "Trung Quân Idol",
					year: "2021",
					imageUrl: "~/assets/images/trungquan.jpg",
					webSrc: 'https://www.nhaccuatui.com/mh/auto/yYUyCwMsNhmR'
			},
	  ],
    Music: [
                    {
                        header: "Nhạc Việt",
                        items: [
                            {
                                imgsrc: "~/assets/images/muonroi.jpg",
                                name: "Muộn Rồi Mà Sao Còn",
                                artist: "Sơn Tùng MTP",
                                webSrc: 'https://www.nhaccuatui.com/bai-hat/muon-roi-ma-sao-con-son-tung-m-tp.6nAqBAZ3nxuV.html'
                            },
                            {
                                imgsrc: "~/assets/images/tractronho.jpg",
                                name: "Trắc Trở",
                                artist: "X2X",
                                webSrc: 'https://www.nhaccuatui.com/bai-hat/trac-tro-x2x.euuuwjUAqLcX.html'
                            },
                            {
                                imgsrc: "~/assets/images/2phut.jpg",
                                name: "2 Phút Hơn",
                                artist: "Pháo",
                                webSrc: 'https://www.youtube.com/watch?v=yoZy2E17-50&list=RDGMEMYH9CUrFO7CfLJpaD7UR85w&start_radio=1&rv=wSxijea-o_M'
                            },
                            {
                                imgsrc: "~/assets/images/chieuthu.jpg",
                                name: "Chiều Thu Họa Bóng Nàng",
                                artist: "DatKaa",
                                webSrc: 'https://www.youtube.com/watch?v=PlVlWl8kKmg'
                            },
                            {
                                imgsrc: "~/assets/images/tuongquan.jpg",
                                name: "Tướng Quân",
                                artist: "Nhật Phong",
                                webSrc: 'https://www.youtube.com/watch?v=wSxijea-o_M&list=RDGMEMYH9CUrFO7CfLJpaD7UR85wVMwSxijea-o_M&start_radio=1'
                            },
                            {
                                imgsrc: "~/assets/images/cogiangtinh.jpg",
                                name: "Cố Giang Tình",
                                artist: "X2X",
                                webSrc: 'https://www.nhaccuatui.com/bai-hat/co-giang-tinh-orinn-remix-x2x.BCYrrDe9HQf5.html'
                            },
                            {
                              name: "Kiếp Thứ II",
                              artist: "Linh Cáo",
                              year: "2020",
                              imgsrc: "~/assets/images/linhcao.jpg",
                              webSrc: 'https://www.youtube.com/watch?v=ADuxk-q745I'
                          },
                          {
                              name: "Yêu Một NGười Sao Buồn Đến Thế",
                              artist: "Noo Phước Thịnh",
                              year: "2020",
                              imgsrc: "~/assets/images/noophuocthinh.jpg",
                              webSrc: 'https://www.nhaccuatui.com/mh/auto/OYEw8BeT2E2P'
                          },
                          {
                              name: "Đôi Mình Bên Nhau",
                              artist: "Linh Cáo",
                              year: "2019",
                              imgsrc: "~/assets/images/doiminhbennhau.jpg",
                              webSrc: 'https://www.nhaccuatui.com/vh/auto/khkDe0WqpBJpf'
                          },
                          {
                              name: "Em Không Sai Chúng Ta Sai",
                              artist: "Erik",
                              year: "2020",
                              imgsrc: "~/assets/images/erik.jpg",
                              webSrc: 'https://www.nhaccuatui.com/vh/auto/8NX7D7ItvnhuQ'
                          },
                          {
                              name: "Đúng Cũng Thành Sai",
                              artist: "Mỹ Tâm",
                              year: "2020",
                              imgsrc: "~/assets/images/mytam.jpg",
                              webSrc: 'https://youtu.be/5_ozB0ImkYA'
                          },
                          {
                              name: "Tình Nào Không Như Tình Đầu",
                              artist: "Trung Quân Idol",
                              year: "202020",
                              imgsrc: "~/assets/images/trungquan.jpg",
                              webSrc: 'https://www.nhaccuatui.com/mh/auto/yYUyCwMsNhmR'
                          },  
                        ],
                    },
                    {
                        header: "Nhạc US-UK",
                        items: [
                            {
                                imgsrc: "~/assets/images/tractronho.jpg",
                                name: "Trắc Trở",
                                artist: "X2X",
                                webSrc: 'https://www.nhaccuatui.com/bai-hat/trac-tro-x2x.euuuwjUAqLcX.html'
                            },
                            {
                                imgsrc: "~/assets/images/2phut.jpg",
                                name: "2 Phút Hơn",
                                artist: "Pháo",
                                webSrc: 'https://www.youtube.com/watch?v=yoZy2E17-50&list=RDGMEMYH9CUrFO7CfLJpaD7UR85w&start_radio=1&rv=wSxijea-o_M'
                            },
                            {
                                imgsrc: "~/assets/images/chieuthu.jpg",
                                name: "Chiều Thu Họa Bóng Nàng",
                                artist: "DatKaa",
                                webSrc: 'https://www.youtube.com/watch?v=PlVlWl8kKmg'
                            },
                            {
                                imgsrc: "~/assets/images/tuongquan.jpg",
                                name: "Tướng Quân",
                                artist: "Nhật Phong",
                                webSrc: 'https://www.youtube.com/watch?v=wSxijea-o_M&list=RDGMEMYH9CUrFO7CfLJpaD7UR85wVMwSxijea-o_M&start_radio=1'
                            },
                            {
                                imgsrc: "~/assets/images/cogiangtinh.jpg",
                                name: "Cố Giang Tình",
                                artist: "X2X",
                                webSrc: 'https://www.nhaccuatui.com/bai-hat/co-giang-tinh-orinn-remix-x2x.BCYrrDe9HQf5.html'
                            },
                            {
                              name: "Kiếp Thứ II",
                              artist: "Linh Cáo",
                              year: "2020",
                              imgsrc: "~/assets/images/linhcao.jpg",
                              webSrc: 'https://www.youtube.com/watch?v=ADuxk-q745I'
                          },
                          {
                              name: "Yêu Một NGười Sao Buồn Đến Thế",
                              artist: "Noo Phước Thịnh",
                              year: "2020",
                              imgsrc: "~/assets/images/noophuocthinh.jpg",
                              webSrc: 'https://www.nhaccuatui.com/mh/auto/OYEw8BeT2E2P'
                          },
                          {
                              name: "Đôi Mình Bên Nhau",
                              artist: "Linh Cáo",
                              year: "2019",
                              imgsrc: "~/assets/images/doiminhbennhau.jpg",
                              webSrc: 'https://www.nhaccuatui.com/vh/auto/khkDe0WqpBJpf'
                          },
                          {
                              name: "Em Không Sai Chúng Ta Sai",
                              artist: "Erik",
                              year: "2020",
                              imgsrc: "~/assets/images/erik.jpg",
                              webSrc: 'https://www.nhaccuatui.com/vh/auto/8NX7D7ItvnhuQ'
                          },
                          {
                              name: "Đúng Cũng Thành Sai",
                              artist: "Mỹ Tâm",
                              year: "2020",
                              imgsrc: "~/assets/images/mytam.jpg",
                              webSrc: 'https://youtu.be/5_ozB0ImkYA'
                          },
                          {
                              name: "Tình Nào Không Như Tình Đầu",
                              artist: "Trung Quân Idol",
                              year: "202020",
                              imgsrc: "~/assets/images/trungquan.jpg",
                              webSrc: 'https://www.nhaccuatui.com/mh/auto/yYUyCwMsNhmR'
                          },  
                        ],
                    },
      ],
      views:0,
      search: '',
      views2:0,
      views1:0,
      music:[]
    };
  },
  methods: {
    // kết nối tới trang mới phát hành và tăng lượt view
    showDetail() {
      this.$navigateTo(Detail);
      this.views += 1;
    },
     // kết nối tới trang Album hot và tăng lượt view
    showDetail1() {
      this.$navigateTo(Detail1);
      this.views1 += 1;
    },
     // kết nối tới trang Topsong và tăng lượt view
    showDetail2() {
      this.$navigateTo(Detail2);
      this.views2 += 1;
    },
     // kết nối tới trang  phát nhạc
    onItemTap(event)
    {
      this.$showModal(SongModal,{
        props:{
          webSrc:event.item.webSrc
        },
      })
    },
    // kết nối phát nhạc cho phần music
    onSong(value){
      this.$showModal(SongModal,{
        props:{
          webSrc:value
        },
      })
    },
     // kết nối tới trang login
    showLogin() {
      this.$navigateTo(Login);
    },
        // kết nối tới trang sign
      showSign() {
      this.$navigateTo(Sign);
    },
    // sap xep thu tu ban chu cai
    doSort() {
      this.Music.forEach((element) => {
        element.items.sort((a, b) => (a.name > b.name ? 1 : -1));
      });
    },
  },
  mounted() {
    this.doSort();
    this.music = this.Music;
  },
  
  computed: {
            filterName() {
                var listproduct = this.Music;
                if (this.search == '') {
                    return listproduct;
                } else {
                    listproduct = [
                        {
                            header: "",
                            items: []
                        },
                        {
                            header: "",
                            items: []
                        }
                    ]
                    for (var i = 0; i < this.Music[0].items.length; i++) {
                        if (this.Music[0].items[i].name.indexOf(this.search) != -1) {
                            listproduct[0].header = this.Music[0].header
                            listproduct[0].items.push(this.Music[0].items[i])
                        }
                    }
                    for (var i = 0; i < this.Music[1].items.length; i++) {
                        if (this.Music[1].items[i].name.indexOf(this.search) != -1) {
                            listproduct[1].header = this.Music[1].header
                            listproduct[1].items.push(this.Music[1].items[i])
                        }
                    }
                    return listproduct;
                }
            }
        }
};
</script>

<style >

.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}
.album-image {
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
ActionBar,
TabStrip 
{
    background-color: #50f0e8;
    color: #FFFFFF;
}

TabStripItem {
    color: #d8dcdd;
}

TabStripItem:active Label {
    color: #f86767;
}

TabStripItem Label {
    font-size: 20;
}

TabContentItem {
    background-color: rgb(255, 255, 255);
}

</style>
