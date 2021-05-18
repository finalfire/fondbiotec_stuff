# Alcuni errori comuni in Python

* [Errori su variabili e funzioni non definite](#errori-su-variabili-e-funzioni-non-definite)
* [Errori con gli indici](#errori-con-gli-indici)
* [Errori di indentazione](#errori-di-indentazione)

## Errori su variabili e funzioni non definite

Accade quando si sbaglia a scrivere il nome corretto. Ad esempio, il seguente codice è errato poiché `print` stampa una variabile non definita: il suo nome è sbagliato, dovrebbe essere `my_var` e non `my_ar`. Questi errori si chiamano `NameError`.

```python
>>> my_var = 5
>>> print(my_ar)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'my_ar' is not defined
>>> 
```

## Errori con gli indici

Per una lista con lunghezza `n` gli indici degli elementi vanno sempre da `0` a `n-1`, e sono detti **indici validi**. Questo vale per tutte le liste. Se proviamo ad accedere ad una lista con degli indici più grandi di `n-1` otterremo un `IndexError`. Il codice seguente itera su di una lista con un ciclo while. La sua condizione indica però `i <= len(l)`: questo significa che `i`, ad un certo punto, sarà uguale a `len(l)`, che non è un indice valido per la lista.

```python
>>> i = 0
>>> l = [4,8,15,16,23,42]
>>> while i <= len(l):
...     print(l[i])
...     i = i+1
... 
4
8
15
16
23
42
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
IndexError: list index out of range
```

## Errori di indentazione

Gli errori di indentazione si hanno quando, all'interno di un blocco di istruzioni (come il corpo di un ciclo o del costrutto `if`) l'indentazione non è corretta su tutto il livello. Con livello si intende il rientro dall'inizio della riga.

Quando si inizia a scrivere un programma, il rientro è sempre a livello 0 (ovvero all'inizio della riga). Se si usa il costrutto `if`, un ciclo oppure si definisce una funzione, il corpo sarà a livello 1 (ovvero una tabulazione dall'inizio della riga); se all'interno di questo corpo si usa un costrutto `if`, un ciclo oppure si definisce una funzione, il corpo sarà a livello 2, e così via.

Il seguente codice mostra un costrutto `if` in cui la seconda istruzione nel corpo ha una indentazione errata. Per sistemarla, basta cancellare gli spazi precedenti l'istruzione e premere il tasto TAB.

```python
>>> x = 42
>>> if x >= 42:
...     print(x)
...  print(x*2)
  File "<stdin>", line 3
    print(x*2)
             ^
IndentationError: unindent does not match any outer indentation level
```

**Attenzione**: una indentazione corretta non è mai un errore sintattico, ma a volte può essere la cartina al tornasole di un errore semantico. Un esempio classico è un ciclo `while` la cui condizione controlla se il valore di una variabile `i` è minore di un certo numero `n`:

```python
i = 0
while i < n:
    print(i)
i = i + 1
```

Questo codice è *sintatticamente corretto*. Seppur corretto, il codice risulta in un ciclo infinito, poiché la variabile `i` deve essere aggiornata all'interno del corpo del ciclo: in questo caso, invece, essa viene aggiornata al di fuori del ciclo, il quale non terminerà mai (perché il valore di `i` sarà sempre pari a `0`). Per fixare questo codice, basta indentare correttamente l'ultima riga all'interno del corpo del ciclo `while`.