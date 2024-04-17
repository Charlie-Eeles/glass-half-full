<template>
  <div class="button-container">
    <button v-for="n in 4" :key="n" @click="handler(n)" :class="'button-' + n">
      {{ ["create", "read", "update", "delete"][n-1] }}
    </button>
  </div>
</template>

<script>
export default {
  methods: {
    async handler(buttonNumber) {
      switch(buttonNumber) {
        case 1:
          await this.postFunc();
          break;
        case 2:
          await this.getFunc();
          break;
        case 3:
          await this.putFunc();
          break;
        case 4:
          await this.deleteFunc();
          break;
        default:
          console.log("Testing function matching clicked button hasn't been implemented");
      }
    },

    async postFunc() {
      try {
        const url = "";
        const data = {};
  
        const res = await fetch(url, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify(data)
        });
        
        const resJson = await res.json();
        console.log(resJson);
      } catch (err) {
        console.error(err);
      }
    },

    async getFunc() {
      try{
        const url = "";
      
        const res = await fetch("");
        const resJson =  await res.json();
        console.log(resJson);
      } catch (err) {
        console.error(err);
      }
    },

    async putFunc() {
      try {
        const url = "";
        const data = {};

        const res = await fetch(url, {
          method: 'PUT',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify(data)
        });
        
        const resJson = await res.json();
        console.log(jsonResponse);
      } catch (err) {
        console.error(err);
      }
    },
   
    async deleteFunc() {
      try {
        const url = "";
      
        const res = await fetch(url, {
          method: 'DELETE'
        });
        
        const resJson = await res.json();
        console.log(resJson);
      } catch (err) {
        console.error(err);
      }
    },

  }
}
</script>

<style>
.button-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}

button {
  background-color: #f0f0f0;
  border: none;
  padding: 10px 20px;
  margin: 10px;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s;
  min-width: 100px;
}

button:hover {
  background-color: #e0e0e0;
  transform: translateY(-2px);
}

</style>
