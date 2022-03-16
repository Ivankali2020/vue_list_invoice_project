<template>
  <div>
    <div class="col-8 m-auto">
      <h1 :class="{ 'text-danger' : getTotal > 5 }"> TOTAL FRUIT : {{ getTotal }}</h1>
      <div class="d-flex mb-4  ">
        <input type="text" v-model="value" class="form-control me-4 ">
        <button @click="add" class="btn btn-success  "  >Add</button>
      </div>
      <ul class="list-group">
        <li v-for="(item,i) in fruits" :key="i" class="list-group-item  animate__animated animate__fadeInDownBig">
          <div>
            <div v-if="item.edit" class="d-flex ">
              <input type="text" :id="`ediabel${i}`"  @keyup.enter="update(item.id)" class="form-control me-4 " v-model="editValue">
              <button @click="update(item.id)" class="btn btn-warning">update</button>
            </div>

            <div  class="d-flex align-items-centel justify-content-between "  v-else>
              <span class="h4 text-capitalize text-secondary" > {{ item.name }}</span>
              <div>
                <button class="btn btn-outline-primary me-3 " :id="i" @click="edit(item)">
                  <i class="bi-pencil"></i>
                </button>
                <button class="btn btn-outline-danger" @click="del(item.id)">
                  <i class="bi-trash"></i>
                </button>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      name : 'ivan',
      count : 1,
      fruits : [
        { id : 1 , name : 'apple' , edit : false  },
        { id : 2 , name : 'orange' , edit : false  },
        { id : 3 , name : 'mango' , edit : false  },
        { id : 4 , name : 'jackFruit' , edit : false  },
      ],
      value : '',
      editValue : '',
    }
  },
  computed: {
    getTotal() {
      return this.fruits.length;
    }
  },
  methods: {
    add() {
      if(this.value.length > 0){
        this.fruits.push({
          id : this.getTotal , name : this.value , edit : false
        });
        this.value = ''
      }else{
        alert('nno daa');
      }
    },
    del(id){
      this.fruits = this.fruits.filter(el => el.id != id);
    },
    edit(i){
      i.edit = !i.edit;
      this.editValue = i.name;
      console.log(i);
    },
    update(id){
      this.fruits.map(el => {
        if(el.id == id){
          el.name = this.editValue;
          el.edit = false;
          console.log(el);
        }
      })
    }
  },
}
</script>

<style scoped>

</style>