<template>
    <div class="app-container">
        <header class="app-header">
            <h1>전화번호부</h1>
        </header>
        <div class="main-content">
            <aside class="sidebar">
                <div class="search-bar">
                    <input type="text" v-model="searchQuery" placeholder="연락처 검색"/>
                </div>
                <ul class="contact-list">
                    <li
                        v-for="contact in filteredContacts"
                        :key="contact.id"
                        @click="selectContact(contact)">
                        {{ contact.name }}
                        <button @click.stop="deleteContact(contact)">삭제</button>
                    </li>
                </ul>
            </aside>
            <section class="contact-details">
                <div v-if="selectedContact">
                    <h2>{{ selectedContact.name }}</h2>
                    <p>전화번호:
                        {{ selectedContact.phone }}</p>
                    <p>이메일:
                        {{ selectedContact.email }}</p>
                </div>
                <div v-else="v-else">
                    <p>연락처를 선택하세요.</p>
                </div>
            </section>
        </div>
        <footer class="app-footer">
            <div class="add-contact">
                <input type="text" v-model="newContact.name" placeholder="이름"/>
                <input type="text" v-model="newContact.phone" placeholder="전화번호"/>
                <input type="text" v-model="newContact.email" placeholder="이메일"/>
                <button @click="addContact">연락처 추가</button>
            </div>
        </footer>
    </div>
</template>

<script setup="setup">
    import {ref, computed} from 'vue';

    const searchQuery = ref('');
    const contacts = ref([
        {
            id: 1,
            name: '홍길동',
            phone: '010-1234-5678',
            email: 'hong@example.com'
        }, {
            id: 2,
            name: '김철수',
            phone: '010-9876-5432',
            email: 'kim@example.com'
        }
    ]);

    const newContact = ref({name: '', phone: '', email: ''});
    const selectedContact = ref(null);

    const filteredContacts = computed(() => {
        return contacts
            .value
            .filter(b => b.name.includes(searchQuery.value));
    });

    const selectContact = a => {
        selectedContact.value = a;
    };

    const addContact = () => {
        if (newContact.value.name && newContact.value.phone && newContact.value.email) {
            contacts
                .value
                .push({
                    ...newContact.value,
                    id: Date.now()
                });
            newContact.value = {
                name: '',
                phone: '',
                email: ''
            };
        }
    };

    const deleteContact = (contact) => {
        contacts.value = contacts
            .value
            .filter(c => c.id !== contact.id);
    };
</script>

<style scoped="scoped">
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