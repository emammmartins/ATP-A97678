```python
# -*- coding:utf-8 -*-
import matplotlib as plt
def getAluno(texto):
    texto.replace("\"","") #exeplo linha 5:[\"a5\"] (queremos tirar as "")
    campos=texto.split(",") 
    aluno=[]
    aluno.append(campos[0])
    aluno.append(campos[1])
    aluno.append(campos[2])
    aluno.append(campos[3:]) #[3:]Cria um lista e assim ja temos lista dentro de lista
    lista=[]
    for s in aluno[3]:
        lista.append(int(s))
    aluno[3]=lista
    return (aluno)

def lerDataset(fnome):
    ficheiro=open(fnome, encoding='latin-1') #nao temos de configurar porque é texto a ser aberto para ler
    bd=[]
    ficheiro.readline() #le a partir da primeira linha
    for linha in ficheiro:
        bd.append(getAluno(linha))# getAluno converte a linha no aluno
    return bd

def chaveOrd(a):
    return a[1]

def listardataset(bd):
    bd.sort(key=chaveOrd)
    print("id        nome       curso      média")
    print("______________________________")
    for a in bd:
        print(a[0] + "|" + a[1] + "|" + a[2] + "|" + str(sum(a[3])/4))
        
def distribPorCurso(bd):
    distribuicao={}
    for a in bd:
        if a[2] in distribuicao.key: #ve se ha uma chave com o curso
            distribuicao[a[2]]+=1
        else:
            distribuicao[a[2]]=1
    return distribuicao
#__________________________Aula_______________________________

def consultarRegisto(bd,chave):
    contar=0
    for linha in bd:
        if linha[0]==chave:
            print(linha[0] + "|" + linha[1] + "|" + linha[2] + "|" + str(sum(linha[3])/4))
            contar=1
    if contar==0:
        print("Nao se encontra registo")
        
def chaveOrd2(a): # a corresponde a uma linha em bd
    return(sum(a[3])/4)
           
def top10(bd):
    bd.sort(key=chaveOrd2,reverse)
    for a in range(10):
        print(bd[a][0] + "|" + bd[a][1] + "|" + bd[a][2] + "|" + str(sum(bd[a][3])/4))
        
def distribPorMedia(bd):
    l=[]
    l1=[] # conta as medias
    l2=[] #conta os alunos
    for linha in bd:
        a=int(sum(linha[3])/4)
        if a in l1:
            p=l1.index(a)
            l2[p]=l2[p]+1
        else:
            l1.append(a)
            l2.append(1)
    for i in range(len(l1)):
        l.append((l1[i],l2[i]))
    print(l)
    return[l1,l2]
        
def plotDistribPorCurso(bd):
    x=[]
    y=[]
    distribuicao=distribPorCurso(bd)
    for i in range(len(distribuicao)):
        x.append(distribuicao[i])
        y.append(distribuicao[i][0])
    plt.bar(x,y,color="red")
    plt.xlabel=x
    plt.ylabel=y
    plt.show()
    
def plotDistribPorMedia(bd):
    lista=distribPorMedia(bd)
    x=lista[0]
    y=lista[1]
    plt.bar(x,y,color="red")
    plt.xlabel=x
    plt.ylabel=y
    plt.show()    
BD=[]
BD=lerDataset("alunos-windows.csv")
#consultarRegisto(BD, "\"a76\"") bem feito(lembrar como pesquisar)
```
