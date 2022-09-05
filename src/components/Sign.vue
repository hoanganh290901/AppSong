<template>
  <Page>
    <ActionBar title="Đăng Ký" />
    <StackLayout class="p-20" backgroundColor="white">
      <Label text="Tên tài khoản:" />
      <TextField
        hint="Name ..."
        style="font-weight: bold; font-size: 20px"
      />
      <Label text="Mật Khẩu:" />
      <TextField
        v-model="city"
        hint="Password..."
        style="font-weight: bold; font-size: 20px"
      />
      <Label text="Nhập Lại Mật Khẩu:" />
      <TextField
        v-model="pass"
        hint="Nhập lại pass..."
        style="font-weight: bold; font-size: 20px"
      />
      <Button class="btn btn-outline" text="Close Modal" @tap="$navigateBack(App)"/>
    </StackLayout>
  </Page>
</template>
<script>
export default {
  data() {
    return {

    };
  },
};
</script>