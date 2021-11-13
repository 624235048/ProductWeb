<template>
  <div class="container">
    <br /><br />
    <div class="row">
      <div>
        <h2>Add New Product</h2>
        <br />
      </div>
    </div>
   <div class="container">

        <div class="form-group row">
            <div class="col">
                <div class="form-group">
                    <label for="productName">ProductName :</label>
                    <input type="text" v-model="product.productName" class="form-control" id="productName" placeholder="Enter productName" name="productName">
                </div>
            </div>
            <div class="form-group row">
           <div class="col">
                <div class="form-group">
                    <label for="productDescription">ProductDescription:</label>
                    <input type="text" v-model="product.productDescription" class="form-control" id="productDescription" placeholder="Enter productDescription" name="productDescription">
                </div>
            </div>
        </div>
            <div class="col">
                <div class="form-group">
                    <label for="productPrice">ProductPrice:</label>
                    <input type="text" v-model="product.productPrice" class="form-control" id="productPrice" placeholder="Enter productPrice" name="productPrice">
                </div>
            </div>
        </div>
        
      <div class="form-group row">
        <div class="col">
          <div class="form-group">
            <label for="productPicture">Upload Image:</label>
            <UploadImage
              id="productPicture"
              name="productPicture"
              ref="productPicture"
            />
          </div>
        </div>
      </div>
      

      <button class="btn btn-primary" v-on:click="SaveBook()">Save</button
      >&nbsp;
      <button class="btn btn-danger" v-on:click="Cancel()">Cancel</button>
    </div>
    <br /><br />
  </div>
</template>

<script>
import UploadImage from "./UploadImage.vue";
import axios from "axios";
//import moment from "moment";
export default {
  name: "AddProduct",
  components: {
    UploadImage,
  },
  data() {
    return {
      accessToken:"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXQiOjE2MzY3NzI3NjAsImV4cCI6MTYzNjc3NjM2MH0.U7jcsogBNICp-z_zYwtFv9v_VldHTPCQry4ZmtQWZrg",
      product: {
        productName: "",
        productDescriotion: "",
        productPrice: 0,
        productPicture : "",
      },
    };
  },
  methods: {
    async SaveBook() {
      if (confirm("Do you want to save this product?")) {

        let productPicture = await this.$refs.productPicture.getFileName();

        if ((await productPicture) !== "") {
          this.product.productPicture = await productPicture;
          await this.$refs.productPicture.UploadImage();
        }

        await axios.post(this.$apiUrl + "product", this.product, {headers: { "Authorization" : `bearer ${this.accessToken}` },});
        await this.$router.push("/product");
      }
    },
    Cancel() {
      if (confirm("Do you want to cancel adding this product?")) {
        this.$router.push("/");
      }
    },
  },
};
</script>

<style scoped>
.book-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

label {
  /* Other styling... */
  text-align: right;
  clear: both;
  float: left;
  margin-right: 15px;
}
</style>
