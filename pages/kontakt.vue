<template>
  <div class="wrapper">
    <FancyImage
      src="/images/RIO|2015, Acryl a. Leinw., 230x270cm.jpeg"
      width="100%"
      height="50vh"
    ></FancyImage>
    <div class="content">
      <h1>Contact</h1>
      <table>
        <tr>
          <td>Email</td>
          <td>example@example.com</td>
        </tr>
        <tr>
          <td>Phone</td>
          <td>+12094343244</td>
        </tr>
        <tr>
          <td>Facebook</td>
          <td>example example</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>

</script>

<style lang="scss" scoped>
table {
  td {
    font-weight: 300 !important;
    color: $text-color;
    padding: 0.4em;
    &:first-child {
      text-align: right;
    }
    &:last-child {
      text-decoration: underline;
    }
  }
}
</style>