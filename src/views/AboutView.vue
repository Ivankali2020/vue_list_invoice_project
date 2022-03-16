<template>
  <div class="about  ">

    <div class="col-lg-8 m-auto">
        <div class="card shadow border-0 mt-3 ">
          <div class="card-title mx-3 text-end ">
            <h1 class="h4  mt-3"> Voucher ID : {{ Math.floor(Math.random() * 100000) }} </h1>
          </div>
          <div class="card-body  d-flex align-items-baseline  justify-content-between">
            <div class="form-group ">
              <label class="form-label">Select Item</label>
              <select class="form-select" aria-label="Default select example"  v-model="select">
                <option disabled value="0">Open this select menu</option>
                <option v-for="item in items" :key="item.id" :value="item.id">
                  {{ item.name }}
                </option>
              </select>
            </div>
            <div  class="form-group ">
              <label class="form-label">Quality</label>
              <input type="text" class="form-control" v-model.number="quality" >
            </div>
            <div class="form-group align-self-end ">
              <button class="btn btn-primary" @click="sum">Add </button>
            </div>
          </div>
        </div>
    </div>
    <div class="col-lg-8 m-auto " v-if="lists.length" >
      <table class="table table-striped mt-5 table-borderless  ">
        <thead>
         <tr>
           <td>Name</td>
           <td>Price</td>
           <td>Quatity</td>
           <td>Total</td>
           <td>Action</td>
         </tr>
        </thead>
        <tbody>
          <tr v-for="list in lists" :key="list.name">
            <td>{{ list.name }}</td>
            <td>{{ list.price }}</td>
            <td>{{ list.qualtity }}</td>
            <td>{{ list.sum }}</td>
            <td>
              <button @click="del(list.id)" class="btn btn-sm btn-outline-danger "><i class="bi-trash"></i></button>
            </td>
          </tr>
        </tbody>
        <tfoot>
        <tr>
          <td colspan="3">TOTAL</td>
          <td>{{ getTotal }}</td>
        </tr>
        </tfoot>
      </table>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        quality: null,
        select : 0,
        items : [
          { name: 'apple'  , price : 40, id : 1},
          { name: 'orange'  , price : 80, id : 2},
          { name: 'mango'  , price : 75, id : 3},
          { name: 'jackfruit'  , price : 66, id : 4},
        ],
        lists : [],
      }
    },
    computed: {
      getTotal() {
        return this.lists.reduce((a,b)=>a+=b.sum,0)
      }
    },
    methods: {
      sum() {
        if(this.quality === null || this.select ===  0 || typeof(this.quality) !== 'number'){
          return alert('you must fill qualtity');
        }
        let selected = this.items.find(el => el.id === this.select);
        selected['qualtity'] = this.quality;
        selected['sum'] = selected.price * this.quality;
        this.lists.push(selected);

      },
      del(id){
        this.lists = this.lists.filter(el => el.id != id);
      }
    },
  }
</script>
