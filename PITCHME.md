# Expresiones Regulares y autómatas finitos

---

<img width="50%" height="50%" data-src="img/chomsky.jpg" style="border-style: none" target="_blank">

---

![chomsky](img/chomsky-hierarchy.png)

---

### Lenguajes

Llamamos _lenguaje_ a un conjunto **finito** de símbolos.

<ul>
	<li class="fragment">$L = \\{0, 1\\}$</li>
	<li class="fragment">$L = \\{a, b\\}$</li>
	<li class="fragment">$L =$ `ASCII`</li>
	<li class="fragment">$L =$ `UTF-8`</li>
</ul>

---

Cuenta el número de hojas en el árbol dado

```haskell
nLeaves :: BinTree a -> Nat
nLeaves tree = intToNat $ length $ leaves tree
```

---

Cuenta el número de nodos internos (ramas) del árbol
SIN hacer recursión directamente

```haskell
nBranches :: BinTree a -> Nat
nBranches tree = intToNat $ n - l
  where
    n = natToInt $ nNodes tree
    l = natToInt $ nLeaves tree
```

**Extra**: implementar `nNodes`.

---


Inserción _a la_ **árbol de búsqueda binaria**

```haskell
insertBST :: (Ord a) =>  a -> BinTree a -> BinTree a
insertBST x BTNil = BTBranch x BTNil BTNil
insertBST x (BTBranch r lchild rchild)
  | x <= r = BTBranch r (insertBST x lchild) rchild
  | otherwise = BTBranch r lchild (insertBST x rchild)
```

---


Pero, ¿qué acaba de ocurrir?

---

- Composición de funciones
- `($) :: (a -> b) -> a -> b` (agrupamiento de expresiones a la derecha)
- Análisis de casos dependiendo de los argumentos del constructor
  (usando notación `|` y `otherwise`).

---

No me gusta cómo Haskell imprime las cosas...

# ¿Cómo _personalizar_ la impresión de tipos de datos?

---

```haskell
instance Show a => Show TipoNuevo where
  show Constructor_1 ... = ...
  show Constructor_2 ... = ...
  .
  .
  .
  show Constructor_m ... = ...
```

Es decir, el `TipoNuevo` se hace instancia de la clase `Show`, que es la
responsable de realizar el **efecto secundario** de imprimir en pantalla.
Finalmente, se define la función `show` cazando todos los patrones del tipo nuevo.

---

### Impresión _elegante_ de árboles binarios

```haskell
instance Show a => Show (BinTree a) where
  show btree = showAux btree ""
    where
      showAux BTNil acc = "Nil"
      showAux (BTBranch r lchild rchild) acc = let newacc = acc ++ "\t"
                                               in "Branch " ++ show r ++
                                                  "\n" ++ newacc ++ showAux rchild newacc ++
                                                  "\n" ++ newacc ++ showAux lchild newacc
```
---

# Ejercicios para puntos extras

---

- Dé una función que calcule el máximo común divisor de dos números enteros.
- Escriba un tipo de datos para representar un árbol binario de tipo genérico
  (`BinTree a`).
- Dada una lista `xs` de tipo `[Char]`, construya la lista de tipo `[BinTree Char]`
  que contiene todos los árboles binarios posibles con los elementos de `xs`
  y que están ordenados (es decir, árboles _de búsqueda binaria_).

---

- Implementar recorridos `preorder`, `inorder` y `postorder`
- Desarrollar un algoritmo de ordenamiento basado en árboles de búsqueda binaria.
- Implementar búsqueda binaria en una lista ordenada

---

### Bibliografía

- http://learnyouahaskell.com/chapters
- https://drive.google.com/file/d/17atMecWDziidvmdX60klMGBnQtOhTQQf/view?usp=sharing
