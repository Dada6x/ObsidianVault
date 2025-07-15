مادة اللغات الصورية (الاوتومات) سنة 3 فصل تاني 















---
# Practical Automat

### {arrow|cyan} Finite Automata 

{arrow} with output :
- Moore Machine 
- Merely Machine


{arrow} without output :
- DFA
- NFA
- Epsilon NFA

---
## DFA (Deterministic Finate Automata) الاتمتة المحددة الحتمية 
- Simplest model of Compution
- Very Limited Memory
Every DFA has these 5

|  Q  | Epsilon | Q0  |  F  | Sigma |
|:---:| ------- |:---:|:---:| ----- |

Q: all states
Epsilon: input  
q0 : the initial state
F: accepted States
sigma :  Transition Function

---
الاوتومات اداه تقوم ب modeling للمشكلة ثم تقوم بحلها 

كيف منعمل DFA لا يقبل سترنغ معين ؟ 
<= منعملها تقبل السترنغ بعدين منعمل كل ستيت عادية ك final state اما الدخل بيضل نفسه 

---
Comparestion betwwen DFA and NFA

| NFA                                           | DFA                             |
| --------------------------------------------- | ------------------------------- |
| an transition or more can be done at one move | only one transition at the move |
| easier to design                              | better for the computer         |
|                                               | harder to design                |

---
> ~={red}Every DFA is an NFA but not **Vise-Versa**  =~
> ~={cyan}But there is an equivalent DFA to every NFA=~

---

| NFA                             | DFA                     |
| ------------------------------- | ----------------------- |
| Sigma = Q * epsilion => 2pow(Q) | sigma = Q* epsilon => Q |

---
`TODO`
##  Converting NFA to DFA
---
##  Converting E-NFA to NFA
---
## Regular Expressions
---
