<template>
  <Page>
     <GridLayout columns="*" rows="80,*" orientation="vertical">
          <Button row=0 class="btn btn-outline" text="Trở Về" @tap="$modal.close()" />
          <!-- lẫy dữ liệu đỗ lên webView -->
          <WebView row=1 :src="webSrc"/>
      </GridLayout>
  </Page>
</template>
<script>
export default {
  props:['webSrc'],
  data() {
    return {
      
    }
  },
}
</script>