```python
# -*- coding:utf-8 -*-
import PySimpleGui as sg

def getEmd(linha):
    # novaLinha=linha.replace("\n","")   opcao para a linha seguinte
    novaLinha = linha.strip("\n")
    emd = []
    campos = novaLinha.split(",")
    emd.append("emd"+str(int(campos[1])+1))
    for i in range(2, len(campos)):
        emd.append(campos[i])
    return emd


def lerDataset(fnome):
    f = open(fnome, encoding="utf-8")
    bd = []
    f.readline()  # tira a linha do cabeçalho
    for linha in f:
        bd.append(getEmd(linha))
    return bd


def chaveOrd(exame):
    return exame[1]


def listarDataset(bd):
    bd.sort(key=chaveOrd, reverse=True)
    print(bd)
    print("id       date        nome               apto")
    print("____________________________________________")
    for linha in bd:
        print(linha[0]+"::"+linha[1]+"::"+linha[2]+" "+linha[3]+"::"+linha[10])


def consultarDataset(bd, id):
    i = 0
    while bd[i][0] != id:
        i = i+1
    return bd[i]

def modalidades(bd):
    l=[]
    for linha in bd:
        if linha[7] not in l:
            l.append(linha[7])
    l.sort()
    return l

def distribPorModalidade(bd):
    distribuicao={}
    for linha in bd:
        if linha[7] in distribuicao.keys():
            distribuicao[linha[7]]=distribuicao[linha[7]]+1
        else:
            distribuicao[linha[7]]=1
    return distribuicao

BD= []
BD= lerDataset("emd.csv")
#___________________________aula________________________________

#tpc: criar um modulo: emd.py
#criar uma interface (por ano,club e modalidade usar tabelas)
'''
import os
print(os.getcwd())    # ajuda a encontar a posicao dos datasets
'''
def distribPorAno(bd):
    distribuicao1={}
    for linha in bd:
        if linha[1] in distribuicao1.keys():
            distribuicao1[linha[1]]=distribuicao1[linha[1]]+1
        else:
            distribuicao1[linha[1]]=1
    return distribuicao1
mypol=[]
coluna1=[[sg.Button("Carregar BD"), font=("Arial",16)]
        [sg.Button("Listar BD"), font=("Arial",16)]
        [sg.Button("Modalidades"), font=("Arial",16)]
        [sg.Button("Listar por ano"), font=("Arial",16)]
        [sg.Button("Listar por modalidades"), font=("Arial",16)]
]
coluna2=[[sg.text(size=(40,2), key="_dados_", font=("Arial",16)]
]
linhasInterface=[
    sg.column(coluna1)
    sg.VSepace()
    sg.column(coluna2)
]
    
sg.Window(default_element_size=(20,1)).Layout(linhasInterface)

stop=False
while not stop:
    event,values=WindowApp.read()
    if event==sg.win_CLOSED:
        stop=True
    if event=="Carregar BD":
        mypol.clear()
        windowApp["_dados_".updates("A base de dados tem", len(BD), "elementos")
    if event=="Listar BD":
        mypol.clear()
        windowApp["_dados_".updates(listarDataset(BD))] 
    if event=="Modalidades":
        mypol.clear()
        windowApp["_dados_".updates(print(modalidades(BD)))]  
    if event=="Listar por Ano":
        mypol.clear()
        windowApp["_dados_".updates(print(distribPorModalidade(BD)))]
    if event=="Listar por Modalidade":
        mypol.clear()
        windowApp["_dados_".updates(print(distribPorAno(BD)))]
                  
window.close()
```
