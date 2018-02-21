# Expresiones Regulares y autómatas finitos

---

<img width="40%" height="40%" data-src="img/chomsky.jpg" style="border-style: none" target="_blank">

---

![chomsky](img/chomsky-hierarchy.png)

---

### Alfabetos

Llamamos _alfabeto_ a un conjunto **finito** de símbolos.

<ul>
	<li class="fragment">$\Sigma = \\{0, 1\\}$</li>
	<li class="fragment">$\Sigma = \\{a, b\\}$</li>
	<li class="fragment">$\Sigma =$ `ASCII`</li>
	<li class="fragment">$\Sigma =$ `UTF-8`</li>
</ul>

---

### Cadenas

Dado un alfabeto $\Sigma$, una _cadena_ es una sucesión **finita** de símbolos
de $L$.

<ul>
	<li class="fragment">
		Si $\Sigma = \\{0, 1\\}$, $01010110$ es una cadena sobre $\Sigma$
	</li>
    <li class="fragment">
		Si $\Sigma = \\{a, b\\}$, $baba$ es una cadena sobre $\Sigma$
	</li>
	<li class="fragment">
		Si $\Sigma =$ `UTF-8`, $hola,$ $soy$ $max$ es una cadena sobre $\Sigma$
	</li>
</ul>

---

### Lenguajes

Un lenguaje $L$ **sobre una alfabeto** $\Sigma$ es un conjunto de cadenas hechas
con símbolos de $\Sigma$.

<ul>
	<li class="fragment">
		Si $\Sigma = \\{0, 1\\}$, $L = \\{0, 1, 001, 01\\}$
	</li>
	<li class="fragment">
		Si $\Sigma =$ `UTF-8`, $L = \\{x\ |\ x$ es un verbo en infinitivo $\\}$
	</li>

</ul>

---
😴 😴 😴 😴 😴
---

## Construyendo lenguajes

---

Sea $\Sigma$ un alfabeto y sea $L$ un lenguaje sobre $\Sigma$.

<ul>
	<li class="fragment">
		Para cualesquiera cadenas $x$ y $w$ de $L$, definimos a la _concatenación_
		de $x$ con $w$ como $z = xw$. Por ejemplo:
		<ul>
			<li class="fragment">
				Si $L = \\{a, b\\}$, $x = aab$ y $w = bba$, entonces
				$z = aabbbba$.
			</li>
		</ul>
	</li>
</ul>

---

Sean $L$ y $M$ dos lenguajes sobre $\Sigma$

<ul>
	<li class="fragment">
		A partir de ahora abreviaremos la notación $L = \\{a\\}$ a únicamente
		$L = a$.
	</li>
	<li class="fragment">
		Definimos la concatenación $LM$ de lenguajes como el lenguaje
		$$LM = \\{xy\ |\  x\text{ es cadena de }L, y\text{ es cadena de }M\\}$$
	</li>
</ul>

---

### La cadena vacía

Denotamos como $\epsilon$ a la cadena _vacía_, es decir, posee la propiedad de

$$w \epsilon = \epsilon w = w$$

para cualquier cadena $w$ sobre un lenguaje $L$.

---

### Suma de lenguajes

Sean $L$ y $M$ dos lenguajes sobre $\Sigma$, definimos la _suma_ de
$L$ con $M$ como el lenguaje formado por la unión de todas las cadenas de
cada lenguaje. Por ejemplo:

<ul>
	<li class="fragment">
		Si $L = \\{0, 1\\}$ y $M = \\{01, 10\\}$; entonces
		$$L + M = \\{0, 1, 01, 10\\}$$
	</li>
	<li class="fragment">
		$a + b = \\{a, b\\}$
	</li>
</ul>

---

Sean $L$ y $M$ dos lenguajes sobre $\Sigma$

<ul>
	<li class="fragment">
		Definimos a la _estrella de Kleeene_ de $L$ como el lenguaje $L^\*$
		que posee todas las posibles cadenas formadas por concatenaciones
		sucesivas de cadenas de $L$
		<ul>
			<li class="fragment">
				Para $L = a$, $L^\* = \\{\epsilon, a, aa, aaa, aaaa, \ldots\\}$
			</li>
			<li class="fragment">
				Para $L = a + b$,
				$$L^\* = \\{\epsilon, a, aa, aaa, aaaa, \ldots,$$
	                     $$b, bb, bbb, bbbb, \ldots,$$
						 $$ab, aab, aaab, aaaab, \ldots,$$
						 $$\ldots,$$
						 $$\ldots\\}$$
			</li>
		</ul>
	</li>
</ul>


---

Finalmente,

## ¡Expresiones Regulares!

---

Sea $\Sigma$ un alfabeto.

<ul>
	<li class="fragment">
		$\epsilon$ es una **expresión regular** sobre $\Sigma$
	</li>
	<li class="fragment">
		Para cualquier $a \in \Sigma$, $a$ es una
		**expresión regular** sobre $\Sigma$
	</li>
	<li class="fragment">
		Si $\alpha$ y $\beta$ son expresiones regulares sobre $\Sigma$, entones
		<ul>
			<li class="fragment">
				$\alpha \beta$ es una **expresión regular** sobre $\Sigma$
			</li>
			<li class="fragment">
				$\alpha^\*$ es una **expresión regular** sobre $\Sigma$
			</li>
		</ul>
	</li>
</ul>
