Для запуску веб-версії у браузері Chrome:

```powershell
flutter run -d chrome
```

## Функції

- Пошук альбомів і виконавців у каталозі Apple Music через відкритий **iTunes Search API** (`country=ua`, з фільтрацією російського контенту); API key не потрібен.
- Каталог показує до 30 результатів одного запиту та підтримує швидкі жанрові фільтри (`українське`, `інді`, `shoegaze`, `dream pop`, `альтернатива`).
- Картка альбому з обкладинкою, жанром, роком, кількістю треків і переходом на сторінку альбому в Apple Music (`url_launcher`).
- Екран виконавця з підбіркою його релізів із каталогу.
- Бібліотека збережених альбомів та щоденник прослуховування: нотатка (до 800 символів), оцінка від 1 до 5 зірок і настрій (`Тепло`, `Ностальгія`, `Спокій`, `Енергія`).
- Дані бібліотеки та нотаток зберігаються локально на пристрої через `SharedPreferences` (`side-a-library-v1`).
- Пошук має стани завантаження, помилки, повторної спроби та відсутніх результатів.

## Архітектура та структура проєкту

- `lib/main.dart` — точка входу, ініціалізація `MultiProvider` (`DiscoverProvider`, `LibraryProvider`), відновлення локальної бібліотеки (`_AppBootstrap`) та кореневий `MaterialApp`.
- `lib/theme/app_theme.dart` — палітра кольорів (`AppColors`), відступи (`AppSpace`) та типографіка (`AppFonts` на базі `google_fonts`: Manrope, Playfair Display, DM Mono).
- `lib/models/` — моделі даних `Album` та `AlbumNote` із серіалізацією JSON.
- `lib/services/itunes_service.dart` — HTTP-клієнт до iTunes Search API з фільтрацією російських виконавців.
- `lib/providers/` — керування станом через `ChangeNotifier` (`DiscoverProvider` для пошуку каталогу та `LibraryProvider` для збережених альбомів і нотаток із синхронізацією у `SharedPreferences`).
- `lib/widgets/` — перевикористовувані компоненти інтерфейсу (`AlbumArtwork`, `AlbumRow`, `PageHeader`, `PressableScale`, `ScreenContainer`, `SectionHeading`).
- `lib/screens/` — екрани застосунку (`MainTabsScreen`, `DiscoverScreen`, `JournalScreen`, `AboutScreen`, `AlbumDetailScreen`, `ArtistScreen`, `NoteEditorScreen`).

## Технології

Flutter, Dart, Provider (`provider`), HTTP (`http`), SharedPreferences (`shared_preferences`), Google Fonts (`google_fonts`), URL Launcher (`url_launcher`).

## Дизайн

Палітра: чистий білий `#FFFFFF`, ніжно-лавандовий `#F5F2FA`, глибокий темно-фіолетовий `#231942` та яскравий фіолетовий акцент `#7C3AED`. Інтерфейс виконаний у фіолетово-білому журнальному стилі з акцентною типографікою.
