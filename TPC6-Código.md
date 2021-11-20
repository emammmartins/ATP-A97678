```python
"Polinómios"

import matplotlib.pyplot as plt

def menu():
    print("""(0)-Sair
(1)-Criar polinómio
(2)-Calcular polinómio
(3)-Apresentar tabela
(4)-Simplificar polinómio
(5)-Calcular a derivada de um polinómio
(6)-Gráfico do polinómio""")

def visual(lista):
    res=""
    if lista==[]: 
        return "0" 
    else:
        for elem in lista:
            c,e=elem
            if res=="":
                res=str(c) + "x^" + str(e)
            else:
                res=res + "+" + str(c) + "x^" + str(e)
    return(res)

def criarTermo():
    a=int(input("Coeficiente:"))
    b=int(input("Expoente:"))
    return(a,b)

def criarPolinomio(l):
    l=[]
    a="s"
    while a=="s":
        a=input("Quer adicionar algum termo?(sim(s) ou n(n)):")
        if a=="s":
            l.append(criarTermo())
        elif a=="n":
            return l
        else:
            print("Erroooooo")
            menu()
            
def calcularPolinomio(l,x):
    total=0
    for elem in l:
        c,e=elem
        cal=(x**e)*c
        total=total+cal
    return total

def simplificarPolinomio(l):
    lista=[]
    maior=l[0][1]
    for elem in l:
        if elem[1]>maior:
            maior=elem[1]
    for i in range(maior+1):
        coe=0
        for elem in l:
            if elem[1]==i:
                coe=coe+elem[0]   
        if coe!=0:
            lista.append((coe,i))
        i=i+1
    lista.reverse()
    return lista

def calcularDerivada(l):
    pol=criarPolinomio(l)
    res=[]
    for (c,e) in pol:
        res.append((c*e,e-1))
    return(res)

def apresentarTabela(l):
    linhas=int(input("Quantas linhas?"))
    for i in range(linhas):
        print((str(i)) + "::" + str(calcularPolinomio(l,i)))
        
def visualGraf(l):
    x=[1,2,3,4,5,6,7,8,9,10]
    y=[]
    conta=0
    for elem in x:
        for ele in l:
            c,e=ele
            conta=conta+(elem**e)*c
        y.append(conta)
        conta=0  
    plt.plot(x,y)
    plt.title("Polinómio")
    plt.show()
  
op=1
while op!=0:
    menu()
    op=int(input("Qual a sua opção:"))
    if op==1:
        print(visual(criarPolinomio([])))
    elif op==2:
        x=int(input("Qual o valor de x?"))
        print(calcularPolinomio(criarPolinomio([]),x))
    elif op==3:
        apresentarTabela(criarPolinomio([]))
    elif op==4:
        print(visual(simplificarPolinomio(criarPolinomio([]))))
    elif op==5:
        print(visual(simplificarPolinomio(calcularDerivada([]))))
    elif op==6:
        print(visualGraf(simplificarPolinomio(criarPolinomio([]))))    
    else:
        print("Errooooo")
print("Até uma próxima")
```
