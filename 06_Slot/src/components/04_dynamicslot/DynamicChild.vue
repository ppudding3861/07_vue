<script setup>
</script>

<template>
    <div class="container">
        <div class="north">
        </div>
        <div class="east">
            <slot name="east">
            </slot>
        </div>
        <div class="west">
            <slot name="west"></slot>
        </div>
        <div class="south">
            <slot name="south"></slot>
        </div>
    </div>
</template>

<style>
.app-container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

.app-header {
  background-color: #007BFF;
  color: white;
  padding: 1rem;
  text-align: center;
}

.main-content {
  display: flex;
  flex: 1;
  overflow: hidden;
}

.sidebar {
  width: 300px;
  background-color: #f8f9fa;
  padding: 1rem;
  overflow-y: auto;
}

.search-bar input {
  width: 100%;
  padding: 0.5rem;
  margin-bottom: 1rem;
  border: 1px solid #ced4da;
  border-radius: 4px;
}

.contact-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.contact-list li {
  padding: 0.5rem;
  cursor: pointer;
  border-bottom: 1px solid #e9ecef;
}

.contact-list li:hover {
  background-color: #e2e6ea;
}

.contact-details {
  flex: 1;
  padding: 1rem;
}

.app-footer {
  background-color: #f8f9fa;
  padding: 1rem;
}

.add-contact input {
  width: calc(100% - 10px);
  margin-bottom: 0.5rem;
  padding: 0.5rem;
  border: 1px solid #ced4da;
  border-radius: 4px;
}

.add-contact button {
  width: 100%;
  padding: 0.5rem;
  background-color: #007BFF;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-contact button:hover {
  background-color: #0056b3;
}
</style>