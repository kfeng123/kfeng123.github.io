---
layout: post
title: "R语言与混合效应模型"
date: 2016-05-10 21:49:50
categories: STAT
--

nlme is the most mature one and comes by default with any R installation. In addition to fitting hierarchical generalized linear mixed models it also allows fitting non-linear ones. Its main advantages are, in my humble opinion, the ability to fit fairly complex hierarchical models using linear or non-linear approaches, a good variety of variance and correlation structures, and access to several distributions and link functions for generalized models. In my opinion, its main drawbacks are 

- fitting cross-classified random factors is a pain

- it can be slow and may struggle with lots of data

- it does not deal with pedigrees by default 

- it does not deal with multivariate data.

lme4 is a project led by Douglas Bates (one of the co-authors of nlme), looking at modernizing the code and making room for trying new ideas. On the positive side, it seems to be a bit faster than nlme and it deals a lot better with cross-classified random factors. Drawbacks: similar to nlme’s, but dropping point i- and adding that it doesn’t deal with covariance and correlation structures yet. It is possible to fit pedigrees using the mmpedigree package, but I find the combination a bit flimsy.

ASReml-R is, unsurprisingly, an R package interface to ASReml. On the plus side it i- deals well with cross-classified random effects, ii- copes very well with pedigrees, iii- can work with fairly large datasets, iv-can run multivariate analyses and v- covers a large number of covariance and correlation structures. Main drawbacks are i- limited functionality for non-Gaussian responses, ii- it does not cover non-linear models and iii- it is non-free (as in beer an speech). The last drawback is relative; it is possible to freely use asreml for academic purposes (and there is also a version for developing countries). Besides researchers, the main users of ASReml/asreml-r are breeding companies.
