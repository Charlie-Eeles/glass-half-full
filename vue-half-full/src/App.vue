<template>
  <div>
    <div v-for="x in 3" :key="x" class="component-container">
      <div class="input-button-container">
        <input placeholder="enter a url..." v-model="this.urls[x]"/>
        <div class="button-group">
          <button v-for="n in 4" :key="n" @click="handler(n, x)">
            {{ ["post", "get", "update", "delete"][n-1] }}
          </button>
        </div>
      </div>
      <textarea placeholder="add a request body..." v-model="bodies[x]"/>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      urls : {},
      bodies: {},
    }
  },
  methods: {
    async handler(buttonNumber, inputKey) {
      switch(buttonNumber) {
        case 1:
          await this.postFunc(inputKey);
          break;
        case 2:
          await this.getFunc(inputKey);
          break;
        case 3:
          await this.putFunc(inputKey);
          break;
        case 4:
          await this.deleteFunc(inputKey);
          break;
        default:
          console.log("Testing function matching clicked button hasn't been implemented");
      }
    },

    async postFunc(urlsKey) {
      try {
        const res = await fetch(this.urls[urlsKey], {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: this.bodies[urlsKey],
          credentials: "include",
        });
        
        const resJson = await res.json();
        console.log(resJson);
      } catch (err) {
        console.error(err);
      }
    },

    async getFunc(urlsKey) {
      try{
        const res = await fetch(this.urls[urlsKey], {credentials: "include"});
        const resJson =  await res.json();
        console.log(resJson);
      } catch (err) {
        console.error(err);
      }
    },

    async putFunc(urlsKey) {
      try {
        const res = await fetch(this.urls[urlsKey], {
          method: 'PUT',
          headers: {
            'Content-Type': 'application/json'
          },
          body: this.bodies[urlsKey],
          credentials: "include"
        });
        
        const resJson = await res.json();
        console.log(jsonResponse);
      } catch (err) {
        console.error(err);
      }
    },
   
    async deleteFunc(urlsKey) {
      try {
        const res = await fetch(this.urls[urlsKey], {
          method: 'DELETE',
          credentials: "include"
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
button {
  background-color: #f0f0f0;
  border: none;
  padding: 10px 20px;
  margin: 5px;
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

.component-container {
  display: flex;
  flex-direction: row;
  margin-bottom: 50px;
  gap: 10px;
  height: 200px;
}

.input-button-container {
  display: flex;
  flex-direction: column;
}

.button-group {
  display: flex;
  flex-direction: column;
}

textarea {
  height: 100%;
  justify-content: space-between;
  width: 300px;
  resize: none;
  padding: 5px;
}

</style>
