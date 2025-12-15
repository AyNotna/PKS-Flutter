# Отчет по практическому заданию № 11
## Белугин Антон Алексеевич
### Контрольная точка №1
Cоздание нового ресурса в mockapi

<img width="609" height="360" alt="image" src="https://github.com/user-attachments/assets/1b44d67a-fef6-4b41-8479-a30f51baaeb6" />

<img width="507" height="309" alt="image" src="https://github.com/user-attachments/assets/9fb812d5-cf1e-4915-bf5c-35a066d4a0b1" />


### Контрольная точка №2
Проект создан, собран и запускается

<img width="505" height="553" alt="image" src="https://github.com/user-attachments/assets/f381be5a-9a5f-41a7-8e57-ac569d705f3f" />

<img width="312" height="534" alt="image" src="https://github.com/user-attachments/assets/d183d08e-d09a-43c4-8357-c716a18cbbe2" />


### Контрольная точка №3
Код модели note
'''dart 
class Note {
  final String id;
  final String title;
  final String body;

  Note({required this.id, required this.title, required this.body});

  factory Note.fromJson(Map<String, dynamic> json) => Note(
    id: json['id'] is String
        ? int.tryParse(json['id']) ?? 0
        : (json['id'] ?? 0),
    title: json['title'] ?? '',
    body: json['body'] ?? '',
  );

  Map<String, dynamic> toJson() => {'id': id, 'title': title, 'body': body};
}
'''
