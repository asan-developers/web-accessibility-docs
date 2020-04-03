# Accessibility API-ları

Web brauzerlər assistiv texnologiyalar faydalı məlumatları ifşa etmək üçün əməliyyat sistemi tərəfindən təqdim edilən xüsusi **accessibility API**-larından istifadə edirlər. Assistiv texnologiyalar daha çox semantik məlumatlardan yararlanır, bu məlumatlara styling və JavaScript daxil deyil. Sözügedən məlumatlar xüsusi ağac (tree) strukturunda formalaşdırılmışdır və **accessibility tree** adlandırılır.

Müxtəlif əməliyyat sistemlərinin müxtəlif API-ları mövcuddur:

- Windows: MSAA/IAccessible, UIAExpress, IAccessible2
- Mac OS X: NSAccessibility
- Linux: AT-SPI
- Android: Accessibility framework
- iOS: UIAccessibility

Nə vaxt ki, HTML tətəfindən təqdim olunan elementlər sizin üçün kifayət etmir, [WAI-ARIA spesifikasiyaların](https://www.w3.org/TR/wai-aria/)dan istifadə etməklə əlavə funksionallıqları tətbiq edə bilərsiniz. WAI-ARIA vasitəsilə siz accessibility tree-yə əlavə məlumatlar yükləyə və kodlarınızı daha da semantik edə bilərsiniz. WAI-ARIA haqqında sonrakı məqalələrdə daha ətraflı danışacağıq.
