<template>
    <ul>

        <form>
            <div class="together">
                <input type="text" placeholder="Název knihy" ref="name">
                <input type="text" placeholder="Autor knihy" ref="author">
            </div>
            <div class="together">
                <input type="number" placeholder="Rok prvního vydání" ref="firstPublished">
                <input type="number" placeholder="Počet stran" ref="pages">
                <input type="number" placeholder="Počet kapitol" ref="chapters">
            </div>
            <button type="submit" @click.prevent="addBook()">Zadat</button>
        </form>
        <transition-group name="fade" tag="ul">
            <li v-for="book in bookList">
                <div class="book-info">
                    <h3>{{ book.name }} - {{ book.firstPublished }}</h3>
                    <p>{{ book.author }}</p>
                    <p><small><i>{{ book.pages }} stran v {{ book.chapters }} kapitolách</i></small></p>
                </div>
                <button @click="removeBook(book)">X</button>
            </li>
        </transition-group>
    </ul>

</template>

<script>

export default {
    data() {
        return {
            bookList: getBooks()
        }
    },

    methods: {
        addBook() {
            if
                (!this.$refs.name.value ||
                !this.$refs.author.value ||
                !this.$refs.firstPublished.value ||
                !this.$refs.pages.value ||
                !this.$refs.chapters.value)
                return;

            this.bookList.unshift({
                name: this.$refs.name.value,
                author: this.$refs.author.value,
                firstPublished: this.$refs.firstPublished.value,
                pages: this.$refs.pages.value,
                chapters: this.$refs.chapters.value
            });
        },

        removeBook(book) {
            this.bookList = this.bookList.filter(books => books !== book);
        },

        getBooks() {
            fetch('../json/books.json').then(response => response.json()).then(json => {
                console.log(json);
                return json;
            });
        }
    }
}
</script>

<style>
h3 {
    margin-bottom: 0;
    margin-top: 0;
}

p {
    margin: 0;
}

form {
    display: flex;
    flex-direction: column;
}

input {
    margin: 1rem;
    margin-top: 0;

    padding: 0.5rem;

}

input::placeholder {
    color: #efefef;
}

button {
    margin-bottom: 1rem;
}

ul {
    padding: 0;
}

li {
    display: flex;
    justify-content: space-between;


    padding: 1rem;
    margin-bottom: 0.25rem;
    border: 2px solid rgba(255, 255, 255, 0.25);
    list-style: none;

    background-color: rgba(255, 255, 255, 0.10);
}

.book-info {
    width: 80%;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>