# Отчет по практическому заданию № 5
## Белугин Антон Алексеевич

### Контрольная точка №1
Список заметок
Отображает список заметок с помощью ListView.builder. Каждая заметка показывается в карточке с заголовком и текстом
```: ListView.builder(
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

Значение счетчика увеличивается на 1 при нажатии кнопки 


### Контрольная точка №3

Счетчик сбрасывается кнопкой "Сбросить"


### Контрольная точка №4

При зажатии кнопки "Увеличить", к счетчику прибавляется 10


### Контрольная точка №5

В коде использовались контейнеры, отступы и другие стили. Все кнопки и названия выровнены


В коде обрабатываются события: нажатие кнопки "Увеличить", долгое нажатие кнопки "Увеличить" и нажатие кнопки "Сбросить".
