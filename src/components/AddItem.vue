
<template>
  <div class="page-container">
    <div class="list-card">
      <h3 class="card-title">Add Item to List</h3>
      
      <div class="input-container">
        <input 
          v-model="newItem" 
          type="text" 
          class="form-input" 
          placeholder="Enter new item" 
          @keyup.enter="addNewItem"
        />
        <button class="add-button" @click="addNewItem">
          <i class="bi bi-plus-lg"></i> Add
        </button>
      </div>

      <div class="list-container">
        <div 
          v-for="(item, index) in items" 
          :key="index" 
          class="list-item"
        >
          <span class="item-text">{{ item }}</span>
          <button 
            @click="removeItem(index)" 
            class="delete-button"
            title="Delete"
          >
            <i class="bi bi-trash"></i> Delete
          </button>
        </div>
        <div 
          v-if="items.length === 0" 
          class="empty-state"
        >
          <i class="bi bi-list-check"></i>
          <p>Your list is empty</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';

export default {
  data() {
    return {
      newItem: ''
    };
  },
  computed: {
    ...mapGetters(['items'])
  },
  methods: {
    ...mapActions(['addItem', 'removeItem']),
    addNewItem() {
      const item = this.newItem.trim();
      if (item) {
        this.addItem(item);
        this.newItem = '';
      }
    }
  }
};
</script>

<style scoped>
    .page-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height:70vh;
  padding: 20px;
  box-sizing: border-box;
  background-color: #f5f7fa;
}

.list-card {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: #ffffff;
  border-radius: 10px;
  box-shadow: 0 8px 16px rgba(0,0,0,0.1);
  padding: 25px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  width: 100%;
  max-width: 500px;
}

.list-card:hover {
  box-shadow: 0 12px 24px rgba(0,0,0,0.15);
  transform: translateY(-2px);
}

.card-title {
  color: #0d5a12;
  font-weight: 600;
  font-size: 1.4rem;
  margin-bottom: 20px;
  text-align: center;
}

.input-container {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.form-input {
  flex: 1;
  padding: 10px 15px;
  border: 1px solid #e0e6ed;
  border-radius: 6px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.form-input:focus {
  outline: none;
  border-color: #1a7a2d;
}

.add-button {
  background-color: #1bd741;
  color: white;
  border: none;
  border-radius: 6px;
  padding: 0 20px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  display: flex;
  align-items: center;
  gap: 5px;
}

.add-button:hover {
  background-color: #3a7843;
}

.list-container {
  border-radius: 6px;
  overflow: hidden;
}

.list-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 15px;
  background-color: #f8fafc;
  border-bottom: 1px solid #e0e6ed;
  transition: all 0.3s ease;
}

.list-item:last-child {
  border-bottom: none;
}

.list-item:hover {
  background-color: #f1f5f9;
  transform: translateX(5px);
}

.item-text {
  color: #447a44;
  font-size: 20px;
  flex-grow: 1;
}

.delete-button {
  background-color: #493f7b;
  color: white;
  border: none;
  border-radius: 6px;
  padding: 6px 12px;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 0.9rem;
}

.delete-button:hover {
  background-color: #2b41c0;
  transform: scale(1.05);
}

.empty-state {
  text-align: center;
  padding: 30px 20px;
  color: #a8b9cf;
  background-color: #f8fafc;
  border-radius: 6px;
}

.empty-state i {
  font-size: 2.5rem;
  margin-bottom: 10px;
  display: block;
}

.empty-state p {
  margin: 0;
  font-size: 1rem;
}
</style>
