# (PART\*) Path Diagrams {-}

# Introduction to Path Diagrams



Path diagrams are a graphical representation of a structural equation model. They are a useful tool for understanding the relationships between variables in a model, as well as a way to communicate the model to others.

In this chapter, we will learn how to create path diagrams using dot notation, as well as explore several software tools available for creating path diagrams, such as `DiagrammeR`, `OpenMx`, and `umx` in R.


## Constructing a Simple Path Diagram


To better understand path diagrams, let's manually construct a simple example. Consider a model where one latent variable influences two observed variables. We can represent this model using the following dot notation:

### Understanding the Components
- **Nodes:** Represent variables, which can be observed or latent. Nodes are usually depicted as circles (latent variables) or squares (observed variables).
- **Edges:** Represent the causal relationships or correlations between variables. An arrow from one node to another indicates a directional relationship, whereas a two-headed arrow indicates a correlation.


### Step-by-Step Construction
1. **Define the Nodes**: Start by defining your nodes, which represent the variables. Here, we have one latent variable and two observed variables.
2. **Draw the Edges**: Next, draw edges to represent the relationships. In this case, the latent variable influences both observed variables.

#### Example Diagram

Let's put these components together using the `DiagrammeR` package to:


``` r
library(DiagrammeR)
grViz("
  digraph simple_model {
    node [fontname = Ariel, fontsize = 10]
    Latent [shape = circle, label = 'Latent Variable L']
    Obs1 [shape = box, label = 'Observed Variable 1']
    Obs2 [shape = box, label = 'Observed Variable 2']
    Latent -> Obs1
    Latent -> Obs2
  }
")
```


```{=html}
<div class="grViz html-widget html-fill-item" id="htmlwidget-ec9a65e7cbc3ba4be891" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-ec9a65e7cbc3ba4be891">{"x":{"diagram":"\n  digraph simple_model {\n    node [fontname = Ariel, fontsize = 10]\n    Latent [shape = circle, label = \"Latent Variable L\"]\n    Obs1 [shape = box, label = \"Observed Variable 1\"]\n    Obs2 [shape = box, label = \"Observed Variable 2\"]\n    Latent -> Obs1\n    Latent -> Obs2\n  }\n","config":{"engine":"dot","options":null}},"evals":[],"jsHooks":[]}</script>
```



This script uses the `DiagrammeR` package to manually create a path diagram where 'Latent Variable L' influences 'Observed Variable 1' and 'Observed Variable 2'. The arrows indicate the direction of influence from the latent to the observed variables.


### ACE Model Example


Here is a more complex example of a path diagram for a univariate ACE model using dot notation and the `DiagrammeR` package in R.


``` r
library(DiagrammeR)
grViz('digraph "Univariate ACE Model" {
	node [style=filled, fontname="Arial", fontsize=16];

	/* Observed Trait */
	Trait [shape=square, fillcolor="#a9fab1", height=0.5, width=0.5, label="Trait"];

	/* Latent Variables */
	A [shape=circle, fillcolor="#f4fd78", label="A"];
	C [shape=circle, fillcolor="#f4fd78", label="C"];
	E [shape=circle, fillcolor="#f4fd78", label="E"];

	/* Paths from Latent Variables to Observed Trait */
	A -> Trait [dir=forward];
	C -> Trait [dir=forward];
	E -> Trait [dir=forward];

	/* Variance Paths for Latent Variables */
	A -> A [dir=both, headport=n, tailport=n];
	C -> C [dir=both, headport=n, tailport=n];
	E -> E [dir=both, headport=n, tailport=n];
}'
)
```


```{=html}
<div class="grViz html-widget html-fill-item" id="htmlwidget-1b45e5cfaacfd34c4bc9" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-1b45e5cfaacfd34c4bc9">{"x":{"diagram":"digraph \"Univariate ACE Model\" {\n\tnode [style=filled, fontname=\"Arial\", fontsize=16];\n\n\t/* Observed Trait */\n\tTrait [shape=square, fillcolor=\"#a9fab1\", height=0.5, width=0.5, label=\"Trait\"];\n\n\t/* Latent Variables */\n\tA [shape=circle, fillcolor=\"#f4fd78\", label=\"A\"];\n\tC [shape=circle, fillcolor=\"#f4fd78\", label=\"C\"];\n\tE [shape=circle, fillcolor=\"#f4fd78\", label=\"E\"];\n\n\t/* Paths from Latent Variables to Observed Trait */\n\tA -> Trait [dir=forward];\n\tC -> Trait [dir=forward];\n\tE -> Trait [dir=forward];\n\n\t/* Variance Paths for Latent Variables */\n\tA -> A [dir=both, headport=n, tailport=n];\n\tC -> C [dir=both, headport=n, tailport=n];\n\tE -> E [dir=both, headport=n, tailport=n];\n}","config":{"engine":"dot","options":null}},"evals":[],"jsHooks":[]}</script>
```


Below is an explanation of the code snippet:

Latent Variables:

- `A [shape=circle, fillcolor="#f4fd78", label="A"];`: Defines the latent variable A (Additive genetic factors) with a circular shape, yellow color (#f4fd78), and the label "A".
- `C [shape=circle, fillcolor="#f4fd78", label="C"];`: Defines the latent variable C (Common/shared environmental factors) with a circular shape, yellow color, and the label "C".
- `E [shape=circle, fillcolor="#f4fd78", label="E"];`: Defines the latent variable E (Unique environmental factors) with a circular shape, yellow color, and the label "E".

Paths from Latent Variables to Observed Trait:

- `A -> Trait [dir=forward];`: Creates a forward directional path from the latent variable A to the observed trait.
- `C -> Trait [dir=forward];`: Creates a forward directional path from the latent variable C to the observed trait.
- `E -> Trait [dir=forward];`: Creates a forward directional path from the latent variable E to the observed trait.

Variance Paths for Latent Variables:

- `A -> A [dir=both, headport=n, tailport=n];`: Represents the variance of the latent variable A with a bidirectional path.
- `C -> C [dir=both, headport=n, tailport=n];`: Represents the variance of the latent variable C with a bidirectional path.
- `E -> E [dir=both, headport=n, tailport=n];`: Represents the variance of the latent variable E with a bidirectional path.

The resulting path diagram visualizes the relationships between the latent variables (A, C, E) and the observed trait in an ACE model.


## Pre-existing software


There are several existing software tools that can be used to create path diagrams for specific models, such as the `umx` and `OpenMx` packages in R. These tools provide a user-friendly interface for creating and visualizing path diagrams, making it easier to understand and communicate complex models.



### Creating a Path Diagram with `omxGraphviz`


``` r
library(OpenMx)
data(demoOneFactor)
manifests <- names(demoOneFactor)
latents <- c("G1")
model1 <- mxModel("One Factor", type="RAM",
    manifestVars = manifests,
    latentVars = latents,
    mxPath(from=latents, to=manifests),
    mxPath(from=manifests, arrows=2),
    mxPath(from=latents, arrows=2, free=F, values=1.0),
    mxData(cov(demoOneFactor), type="cov",numObs=500)
)
omxGraphviz(model1, "one-factor-generated.dot")
```

The following code snippet creates a path diagram for a one-factor model using the OpenMx package. The model includes one latent variable (G1) and three manifest variables (x1, x2, x3). The `mxModel` function is used to define the model, and the `mxPath` function is used to specify the paths between variables. The `mxData` function is used to specify the data for the model. Finally, the `omxGraphviz` function is used to generate a graphical representation of the model in the form of a dot file.

I have annotated the dot file to explain the purpose of each function and argument. The resulting dot file can be visualized using graph visualization tools like Graphviz or packages like `DiagrammeR`.

```
digraph "One Factor" {
  // Setting the style and font for all nodes
  node [style=filled, fontname="Arial", fontsize=16];
  
  /* Manifest Variables */
    // Grouping all manifest variables (x1 to x5) to be on the same rank (horizontal alignment)
  { rank = max; x1; x2; x3; x4; x5 }
  
  // Defining each manifest variable with square shape, color, and size
  x1 [shape=square, fillcolor="#a9fab1", height=0.5, width=0.5];
  x2 [shape=square, fillcolor="#a9fab1", height=0.5, width=0.5];
  x3 [shape=square, fillcolor="#a9fab1", height=0.5, width=0.5];
  x4 [shape=square, fillcolor="#a9fab1", height=0.5, width=0.5];
  x5 [shape=square, fillcolor="#a9fab1", height=0.5, width=0.5];
  
  /* Latent Variables */
    // Defining the latent variable G1 with a circular shape and color
  G1 [shape=circle, fillcolor="#f4fd78"];
  
  /* Paths */
    // Defining directional paths from the latent variable G1 to each manifest variable
  G1 -> x1[dir=forward];
  G1 -> x2[dir=forward];
  G1 -> x3[dir=forward];
  G1 -> x4[dir=forward];
  G1 -> x5[dir=forward];
  
  // Defining bidirectional paths for each manifest variable to represent error terms
  x1 -> x1[dir=both, headport=s, tailport=s];
  x2 -> x2[dir=both, headport=s, tailport=s];
  x3 -> x3[dir=both, headport=s, tailport=s];
  x4 -> x4[dir=both, headport=s, tailport=s];
  x5 -> x5[dir=both, headport=s, tailport=s];
  
  // Defining a bidirectional path for the latent variable G1 to represent its variance
  G1 -> G1[dir=both, headport=n, tailport=n];
}
```

We can load the dot file into R and visualize the path diagram using the `DiagrammeR` package.


``` r

library(DiagrammeR)


grViz("one-factor-generated.dot")
```


```{=html}
<div class="grViz html-widget html-fill-item" id="htmlwidget-a66c4f9e18701c68f604" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-a66c4f9e18701c68f604">{"x":{"diagram":"digraph \"One Factor\" {\n\t node [style=filled, fontname=\"Arial\", fontsize=16];\n \t /* Manifest Variables */\n \t { rank = max; x1; x2; x3; x4; x5 }\n\t x1 [shape=square, fillcolor=\"#a9fab1\", height=0.5, width=0.5];\n\t x2 [shape=square, fillcolor=\"#a9fab1\", height=0.5, width=0.5];\n\t x3 [shape=square, fillcolor=\"#a9fab1\", height=0.5, width=0.5];\n\t x4 [shape=square, fillcolor=\"#a9fab1\", height=0.5, width=0.5];\n\t x5 [shape=square, fillcolor=\"#a9fab1\", height=0.5, width=0.5];\n/* Latent Variables */\n\t G1 [shape=circle, fillcolor=\"#f4fd78\"];\n/* Paths */\n\t G1 -> x1[dir=forward];\n\t G1 -> x2[dir=forward];\n\t G1 -> x3[dir=forward];\n\t G1 -> x4[dir=forward];\n\t G1 -> x5[dir=forward];\n\t x1 -> x1[dir=both, headport=s, tailport=s];\n\t x2 -> x2[dir=both, headport=s, tailport=s];\n\t x3 -> x3[dir=both, headport=s, tailport=s];\n\t x4 -> x4[dir=both, headport=s, tailport=s];\n\t x5 -> x5[dir=both, headport=s, tailport=s];\n\t G1 -> G1[dir=both, headport=n, tailport=n];\n}","config":{"engine":"dot","options":null}},"evals":[],"jsHooks":[]}</script>
```


The resulting path diagram shows the relationships between the latent variable G1 and the manifest variables x1, x2, x3, x4, and x5. The directional paths from G1 to the manifest variables represent the factor loadings, while the bidirectional paths for each manifest variable represent the error terms. The bidirectional path for the latent variable G1 represents its variance.


### Creating a Path Diagram for an ACE Model Using the `umx` Package


The `umx` package provides a user-friendly interface for specifying and estimating structural equation models, including path diagrams for classical models like the ACE model in twin studies. The `umx` package simplifies the process of specifying and estimating complex structural equation models like the ACE model. Below is an example of how to create a path diagram for an ACE model using the `umx` package in R. (Many thanks to Tim Bates for providing the source code). 


``` r
library(umx)
#> For an overview type '?umx'
#> 
#> Attaching package: 'umx'
#> The following object is masked from 'package:stats':
#> 
#>     loadings
```

``` r
library(tidyverse)
# Thanks to Tim Bates for making some nice tidy Source Code
# =====================
# = Make an ACE model =
# =====================
# 1. Clean data: Add separator and scale
data(twinData)
tmp <- umx_make_twin_data_nice(data=twinData, 
                               sep="", zygosity="zygosity", 
                               numbering=1:2) %>% 
  umx_scale_wide_twin_data(varsToScale= c("wt", "ht"), 
                           sep= "_T",
                           data= .)
mzData <- subset(tmp, zygosity %in%  
                   c("MZFF", "MZMM"))
dzData <- subset(tmp, zygosity %in%  
                   c("DZFF", "DZMM"))

# 2. Define paths: You only need the paths for one person:
paths <- c(
  umxPath(v1m0 = c("a1", 'c1', "e1")),
  umxPath(means = c("wt")),
  umxPath(c("a1", 'c1', "e1"), to = "wt", values=.2)
)
m1 <- umxTwinMaker("test", paths, mzData = mzData, dzData = dzData)
#> 6 latent variables were created:a1_T1, c1_T1, e1_T1, a1_T2, c1_T2, e1_T2.
#> 6 latent variables were created:a1_T1, c1_T1, e1_T1, a1_T2, c1_T2, e1_T2.
#> Running test with 4 parameters
#> ?umxSummary options: std=T|F', digits=, report= 'html', filter= 'NS' & more
#> Running Saturated test with 10 parameters
#> Running Independence test with 8 parameters
#> 
#> 
#> Table: (\#tab:unnamed-chunk-5)Parameter loadings for model 'test'
#> 
#> |   |name             | Estimate|SE    |type            |
#> |:--|:----------------|--------:|:-----|:---------------|
#> |8  |a1_T1_MZr_a1_T2  |    1.000|0     |Factor Cov      |
#> |10 |c1_T1_MZr_c1_T2  |    1.000|0     |Factor Cov      |
#> |24 |a1_T1_DZr_a1_T2  |    0.500|0     |Factor Cov      |
#> |26 |c1_T1_DZr_c1_T2  |    1.000|0     |Factor Cov      |
#> |1  |a1_to_wt         |    0.773|0.025 |Factor loading  |
#> |2  |c1_to_wt         |    0.461|0.043 |Factor loading  |
#> |3  |e1_to_wt         |    0.378|0.006 |Factor loading  |
#> |7  |a1_T1_with_a1_T1 |    1.000|0     |Factor Variance |
#> |9  |c1_T1_with_c1_T1 |    1.000|0     |Factor Variance |
#> |11 |e1_T1_with_e1_T1 |    1.000|0     |Factor Variance |
#> |12 |a1_T2_with_a1_T2 |    1.000|0     |Factor Variance |
#> |13 |c1_T2_with_c1_T2 |    1.000|0     |Factor Variance |
#> |14 |e1_T2_with_e1_T2 |    1.000|0     |Factor Variance |
#> |15 |one_to_wt        |   -0.065|0.017 |Mean            |
#> 
#> Model Fit: χ²(6) = 8.64, p = 0.195; CFI = 0.999; TLI = 1; RMSEA = 0.012
```

``` r

plot(m1, std= TRUE, means= FALSE)
#> 
#> ?plot.MxModel options: std, means, digits, strip_zero, file, splines=T/F, min=, max =, same = , fixed, resid= 'circle|line|none'
```


```{=html}
<div class="grViz html-widget html-fill-item" id="htmlwidget-1eaf08e440cd790c33df" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-1eaf08e440cd790c33df">{"x":{"diagram":"digraph G {\n    label=\"MZ\";\n\tsplines=\"TRUE\";\n\t# Latents\n\ta1_T1 [shape = circle];\n\tc1_T1 [shape = circle];\n\te1_T1 [shape = circle];\n\n\t# Manifests\n\twt_T1 [shape = square];\n\n\t#Variances/residuals\n\ta1_T1 -> a1_T1[label=\"@1\", dir=both, headport=n, tailport=n];\n\tc1_T1 -> c1_T1[label=\"@1\", dir=both, headport=n, tailport=n];\n\te1_T1 -> e1_T1[label=\"@1\", dir=both, headport=n, tailport=n];\n\n\n\t# Single arrow paths\n\ta1_T1 -> wt_T1 [label=\"0.79\"];\n\tc1_T1 -> wt_T1 [label=\"0.47\"];\n\te1_T1 -> wt_T1 [label=\"0.39\"];\n\n\t# Covariances\n\n\t{rank=min; a1_T1; c1_T1; e1_T1};\n\t{rank=same; wt_T1};\n\n}","config":{"engine":"dot","options":null}},"evals":[],"jsHooks":[]}</script>
```


The resulting path diagram shows the relationships between the latent variables A, C, and E and the manifest variable `wt`. The paths between the latent variables and manifest variables represent the factor loadings, while the bidirectional paths for each manifest variable represent the error terms. The bidirectional path for each latent variable represents its variance. 

This diagram only shows the paths for one twin, but the model is estimated using data from multiple twin pairs to estimate the genetic, shared environmental, and non-shared environmental influences on the trait. 


