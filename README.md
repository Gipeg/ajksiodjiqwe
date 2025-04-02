class Author:
    def __init__(self, full_name, country):
        self.full_name = full_name
        self.country = country

    def display_info(self):
        print(f"Автор: {self.full_name}, Страна: {self.country}")


class Book:
    def __init__(self, title):
        self.__content = []  # Приватное поле
        self.title = title
        print(f"Книга '{self.title}' создана")

    def __del__(self):
        print(f"Книга '{self.title}' удалена")

    def add_work(self, work):
        self.__content.append(work)

    def get_work_count(self):
        return len(self.__content)

    def display_info(self):
        print(f"Книга: {self.title}\nСодержание:")
        for work in self.__content:
            print(f"- {work}")


class AuthorBook(Author, Book):
    def __init__(self, full_name, country, title):
        Author.__init__(self, full_name, country)
        Book.__init__(self, title)

    def display_full_info(self):
        print(f"Автор: {self.full_name}, Страна: {self.country}")
        print(f"Книга: {self.title}\nСодержание:")
        for work in self._Book__content:
            print(f"- {work}")


# Основная программа
n = int(input("Введите количество авторов: "))
authors_books = []

for _ in range(n):
    name = input("Введите ФИО автора: ")
    country = input("Введите страну автора: ")
    title = input("Введите название книги: ")
    book = AuthorBook(name, country, title)
    works_count = int(input("Сколько произведений в книге? "))
    for _ in range(works_count):
        work = input("Введите название произведения: ")
        book.add_work(work)
    authors_books.append(book)

print("\nСписок всех авторов и их книг:")
for author_book in authors_books:
    author_book.display_full_info()

print("\nСписок русских авторов и их книг:")
for author_book in authors_books:
    if author_book.country.lower() == "россия":
        author_book.display_full_info()
