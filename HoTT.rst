    :Author: Hyungbo Shim

.. contents::



1 Type theory
-------------

1.1 1.1 Type Theory versus Set Theory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- **Equality is a type:** :math:`a=_{A} b` for :math:`a,b : A`. When :math:`a =_{A} b` is inhabited, we say :math:`a` and :math:`b` are **(propositionally) equal**.

- The introduction of **definitional equality**: :math:`a :\equiv b` means :math:`a` is defined to be :math:`b`.

- **Type judgment** :math:`a:A`:

  - When :math:`A:\mathtt{Type}`, :math:`a:A` is pronounced as "the term :math:`a` has type :math:`A`", ":math:`a` is an element of :math:`A`", ":math:`a` is a point of :math:`A`" and ":math:`a` is an object of type :math:`A`".

    - :math:`a:A` may be regarded as analogous to the set theoretic :math:`a\in A` but there is an essential difference that :math:`a:A` is a judgment while :math:`a\in A` is a proposition so that statements like ":math:`(a:A)\Rightarrow (b:B)`" is meaningless.

  - When :math:`A:\mathtt{Prop}`, :math:`a`, in :math:`a:A`, may be called a **witness to the provability** of :math:`A`, or **evidence of the truth** of :math:`A`, or even a **proof** of :math:`A`.

    - :math:`a:A` is **derivable in type theory**, for some :math:`a`, precisely when the analogous judgement ":math:`A` has a proof" is derivable in first-order logic modulo differences in the axioms assumed and in the encoding of mathematics.

- **Judgmental equality**: :math:`\boldsymbol{a\equiv b:A}` means :math:`a` and :math:`b` are definitionally equal objects of type :math:`A`.

- Judgments may depend on **assumptions** of the form :math:`a:A` where :math:`x` is a variable and :math:`A:\mathtt{Type}`. The collection of assumptions is called the **context**.

  - An assumption of the form :math:`x:A:\mathtt{Prop}` is a **hypothesis** that we assume :math:`A:\mathtt{Prop}` holds.

  - Example:

    - :math:`m,n:\mathbb{N}\vdash m+n:\mathbb{N}`.

    - :math:`x,y:A:\mathtt{Type}, p:x=_{A} y\vdash p^{-1}:y=_{A} x`. We may instead say that assuming :math:`x=_{A} y`, we can prove :math:`y=_{A} X`.

  - We CANNOT assume or prove a judgmental equality :math:`x\equiv y` since it is not a type.

  - We may say ":math:`\exists f:A\rightarrow B, f(x)\equiv y`" that is two separate judgments: first, the judgment :math:`f:A\rightarrow B`, then the additional judment :math:`f(x)\equiv y`.

1.2 1.2 Function types
~~~~~~~~~~~~~~~~~~~~~~

- The **function type**: :math:`(A \rightarrow B) : \mathcal{U}`

- The function type of *several variables* is defined by the following equivalent (so that :math:`f(a,b)\equiv f(a)(b)`) methods:

  - by using a cartesian product: :math:`f : (a, b) \mapsto f(a, b) : A \times B \rightarrow C`.

  - by **Currying**: :math:`f: a \mapsto f(a) \mapsto f(a)(b) : A \rightarrow B \rightarrow C`.

- We define :math:`f:a\rightarrow b` by giving an equation :math:`f(x) :\equiv \Phi` where :math:`x:a` is a variable and :math:`\Phi:B` is an expression which may use :math:`x`.

  - Note that :math:`f \not\equiv \Phi`. Instead, :math:`f(x):\equiv\Phi : B` for :math:`x:A` so that :math:`x` is no longer a variable in either :math:`f(x)` or :math:`\Phi` and I should not be writing :math:`\Phi(x)`. In this way, I can write :math:`f(x)[a/x]` or :math:`\Phi[a/x]` for replacing :math:`x` by :math:`a`, that is an :math:`\alpha`-conversion, but it does not make sense to write :math:`f[a/x]`- but if it happens, it should be read as the same as :math:`f(x)[a/x]`.

- **:math:`\boldsymbol{\alpha}`-conversion**: :math:`\lambda x.\, \Phi \rightsquigarrow \lambda y.\, \Phi[y/x]` by the judgmental equality :math:`\lambda x.\, f(x) \equiv \lambda y.\, f(y)`.

- **:math:`\boldsymbol{\lambda}`-abstraction**: for an expression :math:`\Phi`, we can write :math:`(\lambda(x:A).\Phi):A\rightarrow B`. Equivalently, we write

  - :math:`(x\mapsto \Phi):A\rightarrow B`, or

  - :math:`g(x,\_)` for :math:`\lambda y.\, g(x,y)` (**implicit :math:`\boldsymbol{\lambda}`-abstraction**).

  - :math:`\lambda` scope over the rest of the expression unless delimited with parentheses.

    - Example: :math:`\lambda x.\, x+x` is :math:`\lambda x.\, (x+x)` not :math:`(\lambda x.\, x)+x`.

- **:math:`\boldsymbol{\beta}`-reduction** (**computation rule**): :math:`(\lambda x.\,\Phi)(a) \rightsquigarrow \Phi[a/x]` by the definitional equality :math:`(\lambda x.\Phi)(a)` :math:`:\equiv` :math:`\equiv \Phi[a/x]`.

- **:math:`\boldsymbol{\eta}`-expansion**: :math:`f \rightsquigarrow \lambda x.\, f(x)` by the definitional equality :math:`f\equiv (\lambda x.\, f(x))`. This is called the **uniqueness principle for function types** by having :math:`f` uniquely determined by its values.

- A **polymorphic function** is a function that takes a type as one of its arguments and then acts on elements of that type or of other types constructed from it.

  - Example:

    - :math:`\mathtt{id}:\equiv \lambda (A:\mathcal{U}).\, \lambda(x:A).\, x : \prod_{(A:\mathcal{U})} A\rightarrow A`.

      - We can also define :math:`\mathtt{id}` by specifying the argument type :math:`A`: :math:`\mathtt{id}_{A}:\equiv \lambda (x:A).\, x:A\rightarrow A`.

    - :math:`\displaystyle{\mathtt{swap} :\prod_{(A,B,C:\mathcal{U})}  (A\rightarrow B\rightarrow C)\rightarrow (B\rightarrow A\rightarrow C)}` with either

      - :math:`\mathtt{swap}(A,B,C,g):\equiv \lambda b.\, \lambda a.\, g(a)(b)`, or equivalently,

      - :math:`\mathtt{swap}_{A,B,C}(g)(b,a):\equiv g(a,b)`.

1.3 1.3 Universes and families
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- a hierarchy of **universes**: :math:`\mathcal{U}_{0} : \mathcal{U}_{1} : \mathcal{U}_{2} : \cdots`

- the universes are **cumulative** that :math:`A : \mathcal{U}_{i} \Rightarrow A : \mathcal{U}_{i+1}`.

  - We do not identify indices :math:`i` with 'natural numbers :math:`\mathbb{N}` of type theory'. (p.25)

- :math:`A` is a **type** :math:`:= \exists i, A : \mathcal{U}_{i}`. When some universe :math:`\mathcal{U}` is assumed, then types beloning to it is referred as **small types**.

- **Typical ambiguity**: Usually, we omit :math:`i` and write :math:`A : \mathcal{U}`. In this way, we simply write :math:`\mathcal{U} : \mathcal{U}` for :math:`\mathcal{U}_{i} : \mathcal{U}_{i+1}` for any :math:`i`.

- **Family of types** (**type family**): models a collections of types varying over a given type by a function :math:`B : A \rightarrow \mathcal{U}`.

- **constant family type**: given by a constant function :math:`(\lambda (x:A) \, .\, B) : A \rightarrow \mathcal{U}`.

- Non-example: there is no universe large enough to be the codomain of ":math:`\lambda (i:\mathbb{N})\, .\, \mathcal{U}_{i}`".

1.4 1.4 Dependent function types (:math:`\Pi`-types)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Given :math:`A : \mathcal{U}` and a family :math:`B : A \rightarrow \mathcal{U}`, the **dependent function type** :math:`\prod_{(x:A)} B(x) : \mathcal{U}` can be constructed.

  - We may write :math:`\prod_{(x:A)} B(x)`, :math:`\displaystyle{\prod_{(x:A)} B(x)}`, :math:`\prod(x:A),\, B(x)`.

  - If :math:`B` is a constant family, then we fall back to a function type :math:`\prod_{(x:A)} B \equiv (A \rightarrow B)`.

- To define :math:`f:\prod_{(x:A)} B(x)`, we need an expression :math:`\Phi : B(x)`, possibly involving :math:`x:A`, and

  - then write :math:`f(x) :\equiv \Phi` for :math:`x:A`.

  - or use *:math:`\lambda`-abstraction* :math:`\lambda x. \, \Phi  : \prod_{x:A} B(x)`.

- We can **apply** a dependent function :math:`f:\prod_{(x:A)} B(x)` to an argument :math:`a:A` to obtain an element :math:`f(a) : B(a)`.

- :math:`\prod` scope over the rest of the expression unless delimited with parentheses.

  - Example: :math:`\mathtt{id}:\prod_{(a:\mathcal{U})} A\rightarrow A` is :math:`\mathtt{id}: \prod_{(a:\mathcal{U})}(A\rightarrow A)` not :math:`\mathtt{id}:\Big(\prod_{(a:\mathcal{U})}\Big)\rightarrow A`.

- In general, for repeated dependent function type, each domain may depends on the previous one and the codomain may depend on all.

  - Example: :math:`\prod_{(x:A)} \prod_{(y:B(x))} C(x,y)`.

  - But when each argument type are independent from each other, as in :math:`\prod_{(A:\mathcal{U})}\prod_{(B:\mathcal{U})} (A\rightarrow B)\rightarrow (B\rightarrow A)`, we can abbreviate it as :math:`\prod_{(A,B:\mathcal{U})}(A\rightarrow B)\rightarrow (B\rightarrow A)`.

  - Example: The domain of :math:`\mathtt{swap}` is :math:`\prod_{(A:\mathcal{U})} \prod_{(B:\mathcal{U})} \prod_{(C:\mathcal{U})}(A\rightarrow B\rightarrow C)` and we write it simply as :math:`\prod_{(A,B,C:\mathcal{U})}(A\rightarrow B\rightarrow C)`.

1.5 1.5 Product types
~~~~~~~~~~~~~~~~~~~~~

- General pattern for introduction of types:

  1) **formation rules**: how to form new types from old types by the type former.

     - Example: :math:`\cfrac{A:\mathcal{U} \quad B:\mathcal{U}}{A\rightarrow B:\mathcal{U}}`, :math:`\cfrac{A:\mathcal{U} \quad x:A \vdash B(x):\mathcal{U}}{ \big(\prod_{(x:A)}B(x)\big):\mathcal{U}}`.

  2) **introduction rules** (**constructors**): how to inhabit the type

     - Example: :math:`\cfrac{x:A\,\vdash 2x:B}{\vdash \lambda x.\, 2x:A \rightarrow B}`.

  3) **elimination rules** (**eliminators**): how to use elements of the new type.

  4) **computation rule** (**:math:`\boldsymbol{\beta}`-reduction**): how an eliminator acts on a constructor.

  5) **uniqueness principle** (**:math:`\boldsymbol{\eta}`-expansion**): expresses uniqueness of maps into/out of the new type.

     - **propositional uniqueness principle** is when a propositional equality is provable from other rules for the type while the uniqueness principle was not provided as a rule.

2 Formal Type Theory
--------------------

- **contextual judgment**

  - :math:`\Gamma\, \mathtt{ctx}` ; :math:`\Gamma` is well-formed context, that is defined to be a list of judgments :math:`x_{1}:A_{1}, x_{2}:A_{2},\ldots,x_{n}:A_{n}`.

  - Rules:

    - :math:`\cfrac{ }{\cdot \, \mathtt{ctx}}\, \mathtt{ctx}\mathrm{-EMP}`

    - :math:`\cfrac{x_{1}:A_{1},\ldots,x_{n-1}:A_{n-1}\, \vdash A_{n}:\mathcal{U}_{i}}{(x_{1}:A_{1},\ldots,x_{n}:A_{n})\, \mathtt{ctx}}\, \mathtt{ctx}\mathrm{-EXT}`.

- **typing judgment**

  - :math:`\Gamma \, \vdash a:A`

  - Rules:

    - :math:`\cfrac{\Gamma \, \vdash a:A \quad \Gamma, x:A, \Delta \, \vdash b:B}{\Gamma,\Delta[a/x] \, \vdash b[a/x]: B[a/x]}\, \mathtt{Subst}_{\mathtt{1}}`.

    - :math:`\cfrac{\Gamma\, \vdash A:\mathcal{U}_{\mathtt{i}}\quad \Gamma,\Delta\, \vdash b:B}{\Gamma,x:A,\Delta\, \vdash b:B} \, \mathtt{Wkg}_{\mathtt{1}}`.

- **judgmental equality**

  - :math:`\Gamma\,\vdash a\equiv a' : A`.

  - Rules:

    - :math:`\cfrac{\Gamma\, \vdash a:A\quad \Gamma,x:A,\Delta\,\vdash b\equiv c:B}{\Gamma,\Delta[a/x]\, \vdash b[a/x]\equiv c[a/x]:B[a/x]}\, \mathtt{Subst}_{\mathtt{2}}`.

    - :math:`\cfrac{\Gamma\, \vdash A:\mathcal{U}_{i}\quad \Gamma,\Delta\, \vdash b\equiv c:B}{\Gamma,x:A,\Delta\, \vdash b\equiv c:B}\, \mathtt{Wkg}_{\mathtt{2}}`.

  - judgmental equality is an equivalence relation respected by typing:

    - :math:`\cfrac{\Gamma\, a:A}{\Gamma\, a\equiv a:A}` ; (element) reflexivity.

    - :math:`\cfrac{\Gamma\,\vdash a\equiv b:A}{\Gamma\, \vdash b\equiv a:A}` ; (element) symmetricity.

    - :math:`\cfrac{\Gamma\, \vdash a\equiv b:A \quad \Gamma\, \vdash b\equiv c:A}{\Gamma\, \vdash a\equiv c:A}` ; (element) transitivity.

    - :math:`\cfrac{\Gamma\,\vdash a:A\quad \Gamma\,\vdash A\equiv B:\mathcal{U}_{i}}{\Gamma\,\vdash a:B}` ;

    - :math:`\cfrac{\Gamma\,\vdash a\equiv b:A\quad \Gamma\,\vdash A\equiv B:\mathcal{U}_{i}}{\Gamma\,\vdash a\equiv b:B}` ;

- **inference rule**

  - :math:`\cfrac{\mathcal{J}_{1}\quad \cdots \quad \mathcal{J}_k}{\mathcal{J}}\, \mathtt{NAME}` where :math:`\mathcal{J}_{1},\ldots,\mathcal{J}_{n},\mathcal{J}` are judgments not types ; given the **hypotheses** :math:`\mathcal{J}_{1},\ldots,\mathcal{J}_{k}`, the **conclusion** :math:`\mathcal{J}` is derived by :math:`\mathtt{NAME}`.

- **contextual judgment => typing judgment**

  - :math:`\cfrac{ (x_{1}:A_{1},\ldots,x_{n}:A_{n})\, \mathtt{ctx} }{ x_{1}:A_{1},\ldots,x_{n}:A_{n}\, \vdash x_{i}:A_{i}}\, \mathtt{Vble}`.

- **Type universes**: We postulate the exisence of type universes :math:`\mathcal{U}_{0},\mathcal{U}_{1},\mathcal{U}_{2},\ldots` with the following rules:

  - :math:`\cfrac{\Gamma\,\mathtt{ctx}}{\Gamma\, \vdash \mathcal{U}_{i}:\mathcal{U}_{i+1}} \mathcal{U}\mathtt{-INTRO}`

  - :math:`\cfrac{\Gamma\, \vdash A:\mathcal{U}_{i}}{\Gamma\, \vdash A:\mathcal{U}_{i+1}}` :math:`\mathcal{U}`-CUMUL.
