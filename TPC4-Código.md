```python
''' Frações'''
import random
def menu():
    print("""(0)-Sair
(1)-Criar uma fração
(2)-Simplificar fração
(3)-Somar duas frações
(4)-Subtrair duas frações
(5)-Multiplicar duas frações)
(6)-Dividir duas frações
(7)- Gerar uma lista de n fracoes
(8)-Somar as frações de uma lista
(9)-Dizer a maior fração de uma lsita de frações""")
 
def criar():
    numerador=int(input("Qual o numerador?"))
    denominador=int(input("Qual o denominador?"))
    return((numerador,denominador))
    
def mdc(num,den):
    if num<den:
        return mdc(den,num)
    elif num%den==0:
        return den
    else:
        return mdc(num,num%den)

def simplificar(a):
    num,den=a
    div=mdc(num,den)
    return((int(num/div),int(den/div)))

def somar2(a,b):
    n1,d1=a
    n2,d2=b
    return(simplificar((n1*d2+n2*d1,d1*d2)))
    
def subtrair2(a,b):
    n1,d1=a
    n2,d2=b
    return(simplificar((n1*d2-n2*d1,d1*d2)) )
    
def multiplicar2(a,b):
    n1,d1=a
    n2,d2=b
    return(simplificar((n1*n2,d1*d2)))
    
def dividir2(a,b):
    n1,d1=a
    n2,d2=b
    return(simplificar((n1*d2,d1*n2)))
    
def gerar():
    l=[]
    i=1
    n=int(input("Quantas frações deseja gerar?"))
    while i<=n:
        frac=(random.randint(1,100),random.randint(1,100))
        s=simplificar(frac)
        l.append(s)
        i=i+1
    return(l)

def somarF():
    l=gerar()
    print(l)
    soma=l[0]
    i=1
    lista=[]
    for i in range(len(l)-1):
        soma=somar2(soma,l[i])
    lista.append(soma)
    return soma
        

def maior():
    l=gerar()
    print(l)
    maior=l[0]
    i=0
    while i<len(l)-2:
        a1=l[i]
        a2=l[i+1]
        n1=a1[0]
        n2=a2[0]
        d1=a1[1]
        d2=a2[1]
        if n1/d1<n2/d2:
            maior=a2
        i=i+1
    return maior
    
op=1
while op!=0:   
    menu()
    op=int(input("Qual a sua opção:"))
    if op==1:
        print(criar())
    elif op==2:
        a=criar()
        print(a)
        print(simplificar(a))
    elif op==3:
        print("A soma é",simplificar(somar2(criar(),criar())))
    elif op==4:
        print("A diferença é",simplificar(subtrair2(criar(),criar())))
    elif op==5:
        print("A multiplicação é",simplificar(multiplicar2(criar(),criar())))
    elif op==6:
        print("A divisão é",simplificar(dividir2(criar(),criar())))
    elif op==7:
        print(gerar())
    elif op==8:
        print(somarF())
    elif op==9:
        print("Maior=",maior())
    elif op==0:
        print("Obrigada")
    else:
        print("Erro")
        
        
    
  

```
