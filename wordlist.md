# Dead Key — prediction wordlist (Phase 0)

Prediction in Dead Key is a **lookup, not a trained model**. As the user types a partial word, the app matches it as a prefix against this list and shows the top 3 matches, most useful first. English and Arabic lists are separate; the active list follows the Latin / العربية mode toggle.

Rank order = everyday usefulness for someone communicating with one button: needs, people, feelings, time, and common verbs first. Short words rank high because they save the most presses.

## English — top 60

1. yes
2. no
3. please
4. thank
5. thanks
6. help
7. water
8. food
9. hungry
10. thirsty
11. tired
12. pain
13. hurt
14. hot
15. cold
16. bathroom
17. toilet
18. doctor
19. nurse
20. medicine
21. mom
22. dad
23. friend
24. hello
25. hi
26. good
27. morning
28. night
29. today
30. tomorrow
31. now
32. later
33. want
34. need
35. like
36. love
37. happy
38. sad
39. scared
40. okay
41. fine
42. sorry
43. stop
44. go
45. come
46. wait
47. more
48. done
49. home
50. sleep
51. eat
52. drink
53. sit
54. stand
55. walk
56. talk
57. listen
58. read
59. play
60. call

## Arabic — top 60

1. نعم
2. لا
3. من فضلك
4. شكرا
5. ساعدني
6. ماء
7. أكل
8. جوعان
9. عطشان
10. تعبان
11. ألم
12. يؤلمني
13. حار
14. بارد
15. حمام
16. طبيب
17. ممرضة
18. دواء
19. أمي
20. أبي
21. صديق
22. سلام
23. مرحبا
24. صباح الخير
25. مساء الخير
26. اليوم
27. غدا
28. الآن
29. بعد
30. أريد
31. أحتاج
32. أحب
33. سعيد
34. حزين
35. خائف
36. بخير
37. آسف
38. توقف
39. تعال
40. انتظر
41. أكثر
42. انتهيت
43. بيت
44. نوم
45. أكل (verb: آكل)
46. أشرب
47. اجلس
48. قف
49. امش
50. تكلم
51. اسمع
52. اقرأ
53. العب
54. اتصل
55. جيد
56. جميل
57. بسرعة
58. ببطء
59. ممكن
60. مستحيل

## How the lookup works

- Input: the partial word currently being typed (letters accepted so far since the last space).
- Match: words in the active list that start with that partial word (for Arabic, match after folding ة → ت, ى → ي, أ/إ/آ → ا).
- Output: the first 3 matches in rank order. If fewer than 3 match, show only those. If none match, the prediction row stays empty — typing continues normally.
- Accept: tapping a prediction replaces the partial word with the full word, adds a space, and clears the prediction row.
- Note: multi-word phrases in the list (e.g. "من فضلك", "صباح الخير") are accepted as a whole, space included, exactly as listed.
