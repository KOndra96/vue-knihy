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
            bookList: [
                {
                    name: 'Babička',
                    author: 'Božena Němcová',
                    firstPublished: 1855,
                    pages: 270,
                    chapters: 18
                },
                {
                    name: 'Kytice',
                    author: 'Karel Jaromír Erben',
                    firstPublished: 1853,
                    pages: 200,
                    chapters: 13
                },
                {
                    name: 'Máj',
                    author: 'Karel Hynek Mácha',
                    firstPublished: 1836,
                    pages: 100,
                    chapters: 4
                },
                {
                    name: 'Povídky malostranské',
                    author: 'Jan Neruda',
                    firstPublished: 1877,
                    pages: 320,
                    chapters: 13
                },
                {
                    name: 'Osudy dobrého vojáka Švejka za světové války',
                    author: 'Jaroslav Hašek',
                    firstPublished: 1921,
                    pages: 800,
                    chapters: 4
                },
                {
                    name: 'Krakatit',
                    author: 'Karel Čapek',
                    firstPublished: 1924,
                    pages: 350,
                    chapters: 25
                },
                {
                    name: 'Bylo nás pět',
                    author: 'Karel Poláček',
                    firstPublished: 1946,
                    pages: 240,
                    chapters: 10
                },
                {
                    name: 'Zápisky z mrtvého domu',
                    author: 'F. M. Dostojevskij (český překlad)',
                    firstPublished: 1861,
                    pages: 260,
                    chapters: 15
                },
                {
                    name: 'Věci veřejné',
                    author: 'Tomáš Garrigue Masaryk',
                    firstPublished: 1921,
                    pages: 350,
                    chapters: 12
                },
                {
                    name: 'Marketa Lazarová',
                    author: 'Vladislav Vančura',
                    firstPublished: 1931,
                    pages: 300,
                    chapters: 18
                },
                {
                    name: 'Pride and Prejudice',
                    author: 'Jane Austen',
                    firstPublished: 1813,
                    pages: 432,
                    chapters: 61
                },
                {
                    name: 'Moby-Dick',
                    author: 'Herman Melville',
                    firstPublished: 1851,
                    pages: 720,
                    chapters: 135
                },
                {
                    name: 'The Great Gatsby',
                    author: 'F. Scott Fitzgerald',
                    firstPublished: 1925,
                    pages: 218,
                    chapters: 9
                },
                {
                    name: 'Crime and Punishment',
                    author: 'Fyodor Dostoevsky',
                    firstPublished: 1866,
                    pages: 671,
                    chapters: 42
                },
                {
                    name: '1984',
                    author: 'George Orwell',
                    firstPublished: 1949,
                    pages: 328,
                    chapters: 24
                },
                {
                    name: 'To Kill a Mockingbird',
                    author: 'Harper Lee',
                    firstPublished: 1960,
                    pages: 281,
                    chapters: 31
                },
                {
                    name: 'War and Peace',
                    author: 'Leo Tolstoy',
                    firstPublished: 1869,
                    pages: 1225,
                    chapters: 365
                },
                {
                    name: 'The Catcher in the Rye',
                    author: 'J.D. Salinger',
                    firstPublished: 1951,
                    pages: 277,
                    chapters: 26
                },
                {
                    name: 'Brave New World',
                    author: 'Aldous Huxley',
                    firstPublished: 1932,
                    pages: 311,
                    chapters: 18
                },
                {
                    name: 'The Brothers Karamazov',
                    author: 'Fyodor Dostoevsky',
                    firstPublished: 1880,
                    pages: 824,
                    chapters: 96
                },
                {
                    name: 'Don Quixote',
                    author: 'Miguel de Cervantes',
                    firstPublished: 1605,
                    pages: 1072,
                    chapters: 126
                },
                {
                    name: 'One Hundred Years of Solitude',
                    author: 'Gabriel García Márquez',
                    firstPublished: 1967,
                    pages: 417,
                    chapters: 20
                },
                {
                    name: 'Ulysses',
                    author: 'James Joyce',
                    firstPublished: 1922,
                    pages: 730,
                    chapters: 18
                },
                {
                    name: 'Anna Karenina',
                    author: 'Leo Tolstoy',
                    firstPublished: 1878,
                    pages: 864,
                    chapters: 8
                },
                {
                    name: 'The Stranger',
                    author: 'Albert Camus',
                    firstPublished: 1942,
                    pages: 123,
                    chapters: 6
                },
                {
                    name: 'Madame Bovary',
                    author: 'Gustave Flaubert',
                    firstPublished: 1857,
                    pages: 328,
                    chapters: 35
                },
                {
                    name: 'Wuthering Heights',
                    author: 'Emily Brontë',
                    firstPublished: 1847,
                    pages: 416,
                    chapters: 34
                },
                {
                    name: 'The Odyssey',
                    author: 'Homer',
                    firstPublished: -800, // přibližně
                    pages: 541,
                    chapters: 24
                },
                {
                    name: 'Frankenstein',
                    author: 'Mary Shelley',
                    firstPublished: 1818,
                    pages: 280,
                    chapters: 23
                },
                {
                    name: 'The Divine Comedy',
                    author: 'Dante Alighieri',
                    firstPublished: 1320,
                    pages: 798,
                    chapters: 100
                },
                {
                    name: 'The Picture of Dorian Gray',
                    author: 'Oscar Wilde',
                    firstPublished: 1890,
                    pages: 254,
                    chapters: 20
                },
                {
                    name: 'The Metamorphosis',
                    author: 'Franz Kafka',
                    firstPublished: 1915,
                    pages: 64,
                    chapters: 3
                },
                {
                    name: 'Invisible Man',
                    author: 'Ralph Ellison',
                    firstPublished: 1952,
                    pages: 581,
                    chapters: 25
                },
                {
                    name: 'The Old Man and the Sea',
                    author: 'Ernest Hemingway',
                    firstPublished: 1952,
                    pages: 127,
                    chapters: 3
                },
                {
                    name: 'Heart of Darkness',
                    author: 'Joseph Conrad',
                    firstPublished: 1899,
                    pages: 72,
                    chapters: 3
                },
                {
                    name: 'Les Misérables',
                    author: 'Victor Hugo',
                    firstPublished: 1862,
                    pages: 1463,
                    chapters: 365
                },
                {
                    name: 'The Iliad',
                    author: 'Homer',
                    firstPublished: -750, // přibližně
                    pages: 683,
                    chapters: 24
                },
                {
                    name: 'Fahrenheit 451',
                    author: 'Ray Bradbury',
                    firstPublished: 1953,
                    pages: 158,
                    chapters: 3
                },
                {
                    name: 'Dracula',
                    author: 'Bram Stoker',
                    firstPublished: 1897,
                    pages: 418,
                    chapters: 27
                },
                {
                    name: 'Jane Eyre',
                    author: 'Charlotte Brontë',
                    firstPublished: 1847,
                    pages: 500,
                    chapters: 38
                }
            ]
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