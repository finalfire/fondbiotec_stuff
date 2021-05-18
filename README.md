# Alcuni errori comuni in Python

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

## Errori di ndentazionee

