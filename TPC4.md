# **Identificador**: TPC4

#### **Títuro:** Frações

#### **Data início:** 2021-10-25

#### **Data final:** 2021-10-01

#### **Supervisor:** José Carlos Ramalho, https://www.di.uminho.pt/~jcr/thesup-v2.php

#### **Autor** Ema Maria Monteiro Martins, A97678

#### </p> **Resumo:** Este programa consistiu em criar uma série de funções de modo a trabalhar frações. Para isso, fez se uma função "menu" que mostra ao utilizador as operações que pode realizar, sendo elas:</p><p>-Criar uma fração</p><p>-Simplificar uma fração</p><p>-Soma de duas frações</p><p>-Diferença de duas frações</p><p>-Multiplicação de duas frações</p><p>-Divisão de duas frações</p><p>-Gerar uma lista de frações</p><p>-Somar as frações de uma lista de frações</p><p>-Dizer qual a maior fração dada uma lista de frações<p/><p>Apenas algumas funções não foram abordadas na aula pelo que só destas especificarei a sua construção.</p><p>Para criar as 3 primeiras funções, dadas 2 frações, defeniamos 4 variáveis como sendo os numeradores e denominadores das mesma. Posteriormente, na função "dividir2",retornavamos o numerador da primeira a multiplicar pelo denominador da segunda somado com o numerador da segunda a multiplicar pelo denominador da primeira, tudo a dividir pela multiplicação dos denominadores. Na função "multiplicar2" retornavamos o valor dos numeradores a dividir pelos denominadores. Na função "dividir2" multiplicamos o numerador da primeira fração pelo denominador da segunda e dividimos pela multiplicação do denominador da primeira pelo numerador da segunda.</p><p> Na função "gerar" criamos um numerador e um denominador randoms para criar uma fração aleatória.Repetimos o número de fezes que o utilizador definiu como numero de elementos da lista. Adicionamos sempre a uma lista que no final retornamos.</p><p> Com a função "somarF" geramos uma lista aleatória de frações,usando a função "gerar". Definimos uma variável soma (acomulativa) como sendo o primeiro elemento da lista e posteriormente usamos a função "somar2" para ir somando as frações restantes á soma.</p><p>Para realizar a função "maior", começamos por gerar uma lista de frações com auxílio da função "gerar". Em seguida defenimos a menor fração como sendo o primeiro elemento da lista. Vamos comparando os valores da divisão do numerador pelo denominador. Se a divisão da fração seguinte for maior que anterior, então definimos "maior" como sendo essa fração. Por fim, retornamos o valor de "maior".</p><p>Para cada função do menu temos associado um número. Assim, quando o utilizador escolhe o número, chamamos a função correspondente.


```python

```
