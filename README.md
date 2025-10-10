# Отчет по практическому заданию № 5
## Белугин Антон Алексеевич

### Контрольная точка №1
Список заметок
Отображает список заметок с помощью ListView.builder. Каждая заметка показывается в карточке с заголовком и текстом
``` dart
  : ListView.builder(
                    padding: const EdgeInsets.symmetric(
                        horizontal: 20, vertical: 16),
                    itemCount: _notes.length,
                    itemBuilder: (context, index) {
                      final note = _notes[index];
                      final isExpanded = _expandedStates[note.id] ?? false;

                      return Dismissible(
                        key: ValueKey(note.id),
                        direction: DismissDirection.endToStart,
                        background: Container(
                          color: const Color(0xFFFF8627),
                          alignment: Alignment.centerRight,
                          padding: const EdgeInsets.only(right: 20),
                          child: const Icon(Icons.delete, color: Colors.white),
                        ),
                        onDismissed: (direction) => _deleteNote(note),
                        child: Container(
                          margin: const EdgeInsets.only(bottom: 12),
                          decoration: BoxDecoration(
                            color: const Color(0xFFFFAD6D),
                            borderRadius: BorderRadius.circular(12),
                            border: Border.all(
                              color: const Color(0xFF8C582F),
                              width: 1,
                            ),
                          ),
                          child: Material(
                            color: Colors.transparent,
                            child: InkWell(
                              borderRadius: BorderRadius.circular(12),
                              onTap: () => _editNote(note),
                              child: Padding(
                                padding: const EdgeInsets.all(16),
                                child: Column(
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: [
                                    // Заголовок
                                    Text(
                                      note.title.isEmpty
                                          ? 'Name_Your_note'
                                          : note.title,
                                      style: TextStyle(
                                        fontFamily: 'RobotoMono',
                                        fontSize: 16,
                                        fontWeight: FontWeight.w600,
                                        color: const Color(0xFF843A00),
                                      ),
                                    ),
                                    const SizedBox(height: 8),
```


### Контрольная точка №2

Добавление новой заметки
Открывает экран создания новой заметки
```dart
Container(
            width: double.infinity,
            padding: const EdgeInsets.all(20),
            child: ElevatedButton(
              onPressed: _addNote,
              style: ElevatedButton.styleFrom(
                backgroundColor: const Color(0xFFFF8627),
                foregroundColor: Colors.white,
                padding: const EdgeInsets.symmetric(vertical: 16),
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(12),
                ),
                elevation: 0,
              ),
              child: Text(
                'ADD NEW ONE',
                style: TextStyle(
                  fontFamily: 'RobotoMono',
                  fontSize: 16,
                  fontWeight: FontWeight.w600,
                ),
              ),
            ),
          ),
```


### Контрольная точка №3

Редактирование заметки
Открывает экран редактирования существующей заметки
``` dart
Future<void> _addNote() async {
    final newNote = await Navigator.push<Note>(
      context,
      MaterialPageRoute(builder: (_) => const EditNotePage()),
    );

    if (newNote != null) {
      setState(() {
        _notes.add(newNote);
      });
    }
  }

  Future<void> _editNote(Note note) async {
    final updatedNote = await Navigator.push<Note>(
      context,
      MaterialPageRoute(builder: (_) => EditNotePage(existing: note)),
    );
```

### Контрольная точка №4

Удаление заметки с помощью свапа
Позволяет удалить заметку свайпом влево
``` dart
return Dismissible(
                            key: ValueKey(note.id),
                            direction: DismissDirection.endToStart,
                            background: Container(
                              color: Colors.red,
                              alignment: Alignment.centerRight,
                              padding: const EdgeInsets.only(right: 20),
                              child: const Icon(Icons.delete, color: Colors.white),
                            ),
                            onDismissed: (_) => _deleteNote(note),
```

### Контрольная точка №5

Удаление заметки с помощью кнопки
Кнопка корзины в правом углу каждой заметки
``` dart
 IconButton(
                                          onPressed: () => _deleteNote(note),
                                          icon: const Icon(Icons.delete,
                                              size: 18),
```


https://github.com/user-attachments/assets/5218573d-aa1b-47d5-ba85-c9ab0ef4ee39


