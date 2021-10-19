```python
# -*- coding: utf-8 -*-
"""
Menu
"""
import random
def Menu():
    print("""(1)-Introduza a lista á mão
(2)-Gerar lista com valores aleatórios
(3)-Determinar o maior elemento da lista
(4)-Ordenar por ordem crescente uma lista
...
(0)-Sair""")

def CriarListaM():
    n=int(input("Introduza o nº de elementos da lista:"))
    i=1
    l=[]
    while i<n+1:
        a=input("Introduza o número:")
        l.append(a)
        i=i+1
    return l

def CriarListaA():
    n=int(input("Introduza o nº de elementos da lista:"))
    i=1
    l=[]
    while i<n+1:
        a=random.randint(1,100)
        l.append(a)
        i=i+1
    return l

def TrocasDiretas(l):
    i=0
    contar=0
    for i in range(len(l)-1):
        if l[i+1]<l[i]:
            a=l[i+1]
            l[i+1]=l[i]
            l[i]=a
            contar+=1
    if contar!=0:
        TrocasDiretas(l)
    return l
    
def MaiorElemento(l):
    i=0
    maior=l[i]
    while i<len(l)-1:
        a=l[i]
        if a>maior:
            maior=a
        i=i+1
    return maior
    
op=1
while op!=0:
    Menu()      
    op=int(input("Qual a sua opção?"))
    if op==1:
        l=CriarListaM()
        print(l)
    elif op==2:
        l=CriarListaA()
        print(l)
    elif op==3:
        maior=MaiorElemento(l)
        print(maior)
    elif op==4:
        l=TrocasDiretas(l)
        print(l)
    elif op==0:
        print("Até uma próxima")
```
