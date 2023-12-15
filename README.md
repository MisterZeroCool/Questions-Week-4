# <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">Вопросы: Неделя 4!<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
# Содержание
- [Cuncurrency](#cuncurrency)
- [RxJava](#rxjava)
   - [Q1a](#q1a) 
   - [Q2a](#q2a) 
   - [Q3a](#q3a) 
   - [Q4a](#q4a) 
   - [Q5a](#q5a) 
   - [Q6a](#q6a) 
   - [Q7a](#q7a) 
   - [Q8a](#q8a) 
   - [Q9a](#q9a) 
   - [Q10a](#q10a) 
   - [Q11a](#q11a) 
   - [Q12a](#q12a) 
   - [Q13a](#q13a) 
   - [Q14a](#q14a)
   - [Q15a](#q15a) 
   - [Q16a](#q16a) 
   - [Q17a](#q17a) 
   - [Q18a](#q18a) 
   - [Q19a](#q19a) 
   - [Q20a](#q20a) 
   - [Q21a](#q21a)
   - [Q22a](#q22a) 
   - [Q23a](#q23a) 
   - [Q24a](#q24a) 
   - [Q25a](#q25a) 
   - [Q26a](#q26a) 
   - [Q27a](#q27a)
   - [Q28a](#q28a) 
   - [Q29a](#q29a) 
   - [Q30a](#q30a) 
   - [Q31a](#q31a) 
   - [Q32a](#q32a) 
   - [Q33a](#q33a) 
   - [Q34a](#q34a)
   - [Q35a](#q35a) 
   - [Q36a](#q36a) 
   - [Q37a](#q37a) 
   - [Q38a](#q38a) 
   - [Q39a](#q39a)
   - [Q40a](#q40a)
   - [Q41a](#q41a)
   - [Q42a](#q42a)
   - [Q43a](#q43a)
   - [Q44a](#q44a)
   - [Q45a](#q45a)
   - [Q46a](#q35a) 
   - [Q47a](#q36a) 
   - [Q48a](#q37a) 
   - [Q49a](#q38a) 
   - [Q50a](#q39a)
   - [Q51a](#q40a)


## RxJava

- Subjects
  - Publish Subject: Излучает(emit) все последующие элементы наблюдаемого источника в момент подписки.
  - Replay Subject: Излучает(emit все элементы источника наблюдаемого(Observable), независимо от того, когда подписчик(subscriber) подписывается.
  - Behavior Subject: Он излучает(emit) совсем недавно созданый элемент и все последующие элементы наблюдаемого источника, когда наблюдатель(observer) присоединяется к нему.
  - Async Subject: Он выдает только последнее значение наблюдаемого источника(и только последнее). Чтоб его подписчики получили содержание, на сабджекте нужно вызвать onComplete

- flatMap / switchMap / concatMap / concatMapEager
  - `flatMap` не следит за порядком получаемых значений. Для каждого из передаваемых ему значений он создаёт свой observable и может прийти в любом порядке.
  - `switchMap` когда новый объект появлятся из observable выше, он отписывается от остальных — получает только последнее из значений. 
  - `concatMap` похож на `flatMap`, но сохраняет порядок значений. Но есть и минус: `concatMap` ждёт заверешения каждого observable перед переходом к следующему
  - `concatMapEager` похож на `concatMap`, но выполняет код observable асинхронно. Его недостаток: требует больше памяти, чем остальные методы, поэтому для больших стримов использовать аккуратно







