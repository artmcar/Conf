# Практическое занятие №3. Конфигурационные языки

## Задача 1

Реализовать на Jsonnet приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.

###example1.jsonnet
```

local createGroups(prefix, count) = [
  prefix + "-" + std.toString(i) + "-20" for i in std.range(1, count)
];

local studentsInf = [
  {age: 19, group: "ИКБО-4-20", name: "Иванов И.И."},
  {age: 18, group: "ИКБО-5-20", name: "Петров П.П."},
  {age: 18, group: "ИКБО-5-20", name: "Сидоров С.С."},
  {age: 19, group: "ИКБО-67-23", name: "Макарян А.А."}
];


{
  groups: createGroups("ИКБО", 24),
  students: studentsInf,
  subject: "Конфигурационное управление"
}

```
###output.json

```
{
  "groups": [
    "ИКБО-1-20",
    "ИКБО-2-20",
    "ИКБО-3-20",
    "ИКБО-4-20",
    "ИКБО-5-20",
    "ИКБО-6-20",
    "ИКБО-7-20",
    "ИКБО-8-20",
    "ИКБО-9-20",
    "ИКБО-10-20",
    "ИКБО-11-20",
    "ИКБО-12-20",
    "ИКБО-13-20",
    "ИКБО-14-20",
    "ИКБО-15-20",
    "ИКБО-16-20",
    "ИКБО-17-20",
    "ИКБО-18-20",
    "ИКБО-19-20",
    "ИКБО-20-20",
    "ИКБО-21-20",
    "ИКБО-22-20",
    "ИКБО-23-20",
    "ИКБО-24-20"
  ],
  "students": [
    {
      "age": 19,
      "group": "ИКБО-4-20",
      "name": "Иванов И.И."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Петров П.П."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Сидоров С.С."
    },
    {
      "age": 19,
      "group": "ИКБО-67-23",
      "name": "Макарян А.А."
    }
  ],
  "subject": "Конфигурационное управление"
}
```

## Задача 2

Реализовать на Dhall приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.

```
{
  "groups": [
    "ИКБО-1-20",
    "ИКБО-2-20",
    "ИКБО-3-20",
    "ИКБО-4-20",
    "ИКБО-5-20",
    "ИКБО-6-20",
    "ИКБО-7-20",
    "ИКБО-8-20",
    "ИКБО-9-20",
    "ИКБО-10-20",
    "ИКБО-11-20",
    "ИКБО-12-20",
    "ИКБО-13-20",
    "ИКБО-14-20",
    "ИКБО-15-20",
    "ИКБО-16-20",
    "ИКБО-17-20",
    "ИКБО-18-20",
    "ИКБО-19-20",
    "ИКБО-20-20",
    "ИКБО-21-20",
    "ИКБО-22-20",
    "ИКБО-23-20",
    "ИКБО-24-20"
  ],
  "students": [
    {
      "age": 19,
      "group": "ИКБО-4-20",
      "name": "Иванов И.И."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Петров П.П."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Сидоров С.С."
    },
    <добавьте ваши данные в качестве четвертого студента>
  ],
  "subject": "Конфигурационное управление"
} 
```

```
let Student = { age : Natural, group : Text, name : Text }

let Group = Text

let groupPrefix = "ИКБО-"

let groupYear = "-20"
let groupYear1 = "-23"

let makeGroup1 =
	  λ(n : Natural) →
        groupPrefix  ++ Natural/show n ++ groupYear1

let groups1 = [ makeGroup1 67]

let makeGroup =
      λ(n : Natural) →
        groupPrefix ++ Natural/show n ++ groupYear

let groups =
      [ makeGroup 1, makeGroup 2, makeGroup 3, makeGroup 4, makeGroup 5
      , makeGroup 6, makeGroup 7, makeGroup 8, makeGroup 9, makeGroup 10
      , makeGroup 11, makeGroup 12, makeGroup 13, makeGroup 14, makeGroup 15
      , makeGroup 16, makeGroup 17, makeGroup 18, makeGroup 19, makeGroup 20
      , makeGroup 21, makeGroup 22, makeGroup 23, makeGroup 24
      ]

let students =
      [ { age = 19, group = makeGroup 4, name = "Иванов И.И." }
      , { age = 18, group = makeGroup 5, name = "Петров П.П." }
      , { age = 18, group = makeGroup 5, name = "Сидоров С.С." }
      , { age = 19, group = makeGroup1 67, name = "Макарян А.А." }
      ]

let subject = "Конфигурационное управление"

in  { groups = groups, groups1 = groups1, students = students, subject = subject }
```
```
{
  "groups": [
    "ИКБО-1-20",
    "ИКБО-2-20",
    "ИКБО-3-20",
    "ИКБО-4-20",
    "ИКБО-5-20",
    "ИКБО-6-20",
    "ИКБО-7-20",
    "ИКБО-8-20",
    "ИКБО-9-20",
    "ИКБО-10-20",
    "ИКБО-11-20",
    "ИКБО-12-20",
    "ИКБО-13-20",
    "ИКБО-14-20",
    "ИКБО-15-20",
    "ИКБО-16-20",
    "ИКБО-17-20",
    "ИКБО-18-20",
    "ИКБО-19-20",
    "ИКБО-20-20",
    "ИКБО-21-20",
    "ИКБО-22-20",
    "ИКБО-23-20",
    "ИКБО-24-20"
  ],
  "groups1": [
    "ИКБО-67-23"
  ],
  "students": [
    {
      "age": 19,
      "group": "ИКБО-4-20",
      "name": "Иванов И.И."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Петров П.П."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Сидоров С.С."
    },
    {
      "age": 19,
      "group": "ИКБО-67-23",
      "name": "Макарян А.А."
    }
  ],
  "subject": "Конфигурационное управление"
}
```


Для решения дальнейших задач потребуется программа на Питоне, представленная ниже. Разбираться в самом языке Питон при этом необязательно.

```Python
import random


def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)


BNF = '''
E = a
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))

```

Реализовать грамматики, описывающие следующие языки (для каждого решения привести БНФ). Код решения должен содержаться в переменной BNF:

## Задача 3

Язык нулей и единиц.

```
import random

def parse_bnf(text):
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)


BNF = '''
E = 0 | 1 | E E
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))

```

```
0
01
1
1
11110
0
1
1000
0
1
```

## Задача 4

Язык правильно расставленных скобок двух видов.

```

import random

def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)

BNF = '''
E = ( E ) | { E } | E E |
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))

```

```
{{{{{}({})}}}}

(({(({{}}))}))
{{({})}}
{{((((((()))))))}}

{({(())})}
{{{{({()}{})}((()))}}(({({(){}}((())){((({})){{{()}(((({}))))}}{})})}{}()()))}
((((()))))
```

## Задача 5

Язык выражений алгебры логики.

```

import random

def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)

BNF = '''
E = ( E ) | E & E | E | E | ~ E | x | y
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))
```



```
(x)
(((~(((x)))&(x)&(~y))))
(((~x)&y))
~x
~(x)
x
(y)
x
~y
```

