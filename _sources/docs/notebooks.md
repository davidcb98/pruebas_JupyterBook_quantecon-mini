---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.15.2
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# Content with notebooks

+++

> {sub-ref}`today` | {sub-ref}`wordcount-words` words | {sub-ref}`wordcount-minutes` min read

+++

You can also create content with Jupyter Notebooks. This means that you can include
code blocks and their outputs in your book.

## Markdown + notebooks

As it is markdown, you can embed images, HTML, etc into your posts!

![](https://myst-parser.readthedocs.io/en/latest/_static/logo-wide.svg)

You can also $add_{math}$ and

$$
\begin{aligned}
\mbox{mean} la_{tex} \\ \\
math blocks
\end{aligned}
$$

But make sure you \$Escape \$your \$dollar signs \$you want to keep!

## MyST markdown

MyST markdown works in Jupyter Notebooks as well. For more information about MyST markdown, check
out [the MyST guide in Jupyter Book](https://jupyterbook.org/content/myst.html),
or see [the MyST markdown documentation](https://myst-parser.readthedocs.io/en/latest/).

## Code blocks and outputs

Jupyter Book will also embed your code blocks and output in your book.
For example, here's some sample Matplotlib code:

```{code-cell} ipython3
from matplotlib import rcParams, cycler
import matplotlib.pyplot as plt
import numpy as np
plt.ion()
```

```{code-cell} ipython3
# Fixing random state for reproducibility
np.random.seed(19680801)

N = 10
data = [np.logspace(0, 1, 100) + np.random.randn(100) + ii for ii in range(N)]
data = np.array(data).T
cmap = plt.cm.coolwarm
rcParams['axes.prop_cycle'] = cycler(color=cmap(np.linspace(0, 1, N)))


from matplotlib.lines import Line2D
custom_lines = [Line2D([0], [0], color=cmap(0.), lw=4),
                Line2D([0], [0], color=cmap(.5), lw=4),
                Line2D([0], [0], color=cmap(1.), lw=4)]

fig, ax = plt.subplots(figsize=(10, 5))
lines = ax.plot(data)
ax.legend(custom_lines, ['Cold', 'Medium', 'Hot']);
```

There is a lot more that you can do with outputs (such as including interactive outputs)
with your book. For more information about this, see [the Jupyter Book documentation](https://jupyterbook.org)

+++

## Ejemplo de ecuaciones numeradas con referencias 

+++

\begin{equation} 
f(x) = x^2 
\end{equation} 

+++

En la Ec. podemos ver un una función cuadrática

+++

$$
  w_{t+1} = (1 + r_{t+1}) s(w_t) + y_{t+1}
$$ (my_other_label)

+++

- A link to a dollar math block: {eq}`my_other_label`

+++

```{math} 
:label: euler
e^{i\pi} + 1 = 0
```

+++

Refereciemos la ec. de euler {eq}`euler`.


+++

## Roles and directives

+++

Basicamente son funciones. https://myst-parser.readthedocs.io/en/latest/syntax/roles-and-directives.html#syntax-directives

+++

### Cuadros (usando comillas)

+++

```{admonition} This is an admonition
This is an admonition
```

+++

```{admonition} This is an admonition class note
:class: note
This is an admonition class note
```

+++

```{admonition} This is an admonition class important
:class: important

This is an admonition class important
```

+++

```{admonition} This is an admonition class warning
:class: warning

This is an admonition class warning
```

+++

```{note}
This a note (no se puede cambiar el titulo)
```

+++

```{warning}
This is a warning (no se puede cambiar el título)
```

+++

````{note}
The next info should be nested
```{warning}
Here's my warning
```
````

+++

### Cuadros (usando ::: :::)

+++

::::{important} 
:::{note}

This text is **standard** _Markdown_ 
Cuadro 1
:::
::::

+++

:::{admonition} Cuadro de Warning
:class: warning

This text is **standard** _Markdown_
Cuadro 3
:::

+++

### Code blocks

+++

```{code-block} python
:lineno-start: 10  # this is a comment
: # this is also a comment
:emphasize-lines: "1, 3"
:caption: |
:    This is my
:    multi-line caption. It is *pretty nifty* ;-)

a = 2
print('my 1st line')
print(f'my {a}nd line')
```

+++

## Referencias a secciones

+++

Vamos a referenciar la sección de las ecuaciones [](#content-with-notebooks)

+++

## Figuras

+++

:::{figure-md} 
:class: myclass
:name: fig-target
<img src="Figuras/Descomp_ortogonal.png" 
     alt="decipcion de la imagen" 
     class="bg-primary mb-1" 
     width="200px"
     align="center">

This is a caption in **Markdown**
:::

Align options: “top”, “middle”, “bottom”, “left”, “center”, or “right”

+++

Referencia a la figura: [Go to the graph!](#fig-target)

+++

```{figure} Figuras/Descomp_ortogonal.png
:scale: 50 %
:alt: map to buried treasure
:name: fig-target-2

This is the caption of the figure (a simple paragraph).
```

+++

Referencia a la figura: [Go to the graph 2!](#fig-target-2)
