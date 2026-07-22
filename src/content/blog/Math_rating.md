---
title: Is Euler really the greatest?
type: own-articles
status: draft
date_published: 2026-07-19
date_updated:
published: false
excerpt: A network analysis of 96 great mathematicians reveals that Euler, despite his reputation, isn't the most central figure — and the reason why says something about how we assign credit in general.
slug: is-euler-really-the-greatest
url:
review_count: 0
tags:
  - type/own-articles
  - project/blog
topics:
  - mathematics
  - graph-theory
  - data-science
created: 2026-07-19T16:47
updated: 2026-07-22T14:59
---

# Is Euler really the greatest?

## Overview

An analysis of mathematical influence through network analysis of 96 great mathematicians from "The Princeton Companion to Mathematics."

## Key Points

- Euler remains a top-tier influence, but not the outright #1 in this network
- Network analysis reveals unexpected influence patterns — Abel and Hilbert challenge the usual narrative 
- Graph theory provides insights into mathematical lineage, and into how credit and centrality diverge
## Main Content

A few weeks ago, someone told me: "Everything in mathematics could eventually be named after Euler, because he was truly the greatest". First of all, I'm not a mathematician at all, so I'm not the person to argue about this. But I am truly interested in mathematics, especially when they are related to IT in general, and more specifically graph theory, data science and deep learning in particular. And already with this basic math knowledge, I have to admit that Euler was truly one of the greatest mathematicians of all time.

But: was he truly the greatest? Triggered by my interest for graph theory, I did a small experiment. I found a list of 96 mathematicians in "The Princeton Companion to Mathematics", a book by Timothy Gowers, University of Cambridge. Then I looked up these 96 mathematicians on Wikipedia, and wrote a program to count the number of links to the others. Doing so, I could make a ranking of the most central mathematicians within this network of 96 - not "of all time", but relative to each other, based purely on how their Wikipedia pages link together. 

First of all, the list of mathematicians:

| #   | Name                                      | Years        |
| --- | ----------------------------------------- | ------------ |
| 1   | Pythagoras                                | ca. 569 B.C. |
| 2   | Euclid                                    | ca. 325 B.C. |
| 3   | Archimedes                                | ca. 287 B.C. |
| 4   | Apollonius                                | ca. 262 B.C. |
| 5   | Abu Ja'far Muhammad ibn Mūsā al-Khwārizmī | 800 - 847    |
| 6   | Leonardo of Pisa (known as Fibonacci)     | 1170 - 1250  |
| 7   | Girolamo Cardano                          | 1501 - 1576  |
| 8   | Rafael Bombelli                           | 1526 - 1572  |
| 9   | François Viète                            | 1540 - 1603  |
| 10  | Simon Stevin                              | 1548 - 1620  |
| 11  | René Descartes                            | 1596 - 1650  |
| 12  | Pierre Fermat                             | 1600 - 1665  |
| 13  | Blaise Pascal                             | 1623 - 1662  |
| 14  | Isaac Newton                              | 1642 - 1727  |
| 15  | Gottfried Wilhelm Leibniz                 | 1646 - 1716  |
| 16  | Brook Taylor                              | 1685 - 1731  |
| 17  | Christian Goldbach                        | 1690 - 1764  |
| 18  | The Bernoullis                            | -            |
| 19  | Leonhard Euler                            | 1707 - 1783  |
| 20  | Jean Le Rond d'Alembert                   | 1717 - 1783  |
| 21  | Edward Waring                             | 1735 - 1798  |
| 22  | Joseph Louis Lagrange                     | 1736 - 1813  |
| 23  | Pierre-Simon Laplace                      | 1749 - 1827  |
| 24  | Adrien-Marie Legendre                     | 1752 - 1833  |
| 25  | Jean Baptiste Joseph Fourier              | 1768 - 1830  |
| 26  | Carl Friedrich Gauss                      | 1777 - 1855  |
| 27  | Siméon-Denis Poisson                      | 1781 - 1840  |
| 28  | Bernard Bolzano                           | 1781 - 1848  |
| 29  | Augustin-Louis Cauchy                     | 1789 - 1857  |
| 30  | August Ferdinand Möbius                   | 1790 - 1868  |
| 31  | Nicolai Ivanovich Lobachevskii            | 1792 - 1856  |
| 32  | George Green                              | 1793 - 1841  |
| 33  | Niels Henrik Abel                         | 1802 - 1829  |
| 34  | János Bolyai                              | 1802 - 1860  |
| 35  | Carl Gustav Jacob Jacobi                  | 1804 - 1851  |
| 36  | Peter Gustav Lejeune Dirichlet            | 1805 - 1859  |
| 37  | William Rowan Hamilton                    | 1805 - 1865  |
| 38  | Augustus De Morgan                        | 1806 - 1871  |
| 39  | Joseph Liouville                          | 1809 - 1882  |
| 40  | Ernst Eduard Kummer                       | 1810 - 1893  |
| 41  | Évariste Galois                           | 1811 - 1832  |
| 42  | James Joseph Sylvester                    | 1814 - 1897  |
| 43  | George Boole                              | 1815 - 1864  |
| 44  | Karl Weierstrass                          | 1815 - 1897  |
| 45  | Pafnuty Chebyshev                         | 1821 - 1894  |
| 46  | Arthur Cayley                             | 1821 - 1895  |
| 47  | Charles Hermite                           | 1822 - 1901  |
| 48  | Leopold Kronecker                         | 1823 - 1891  |
| 49  | Georg Friedrich Bernhard Riemann          | 1826 - 1866  |
| 50  | Julius Wilhelm Richard Dedekind           | 1831 - 1916  |
| 51  | Émile Léonard Mathieu                     | 1835 - 1890  |
| 52  | Camille Jordan                            | 1838 - 1922  |
| 53  | Sophus Lie                                | 1842 - 1899  |
| 54  | Georg Cantor                              | 1845 - 1918  |
| 55  | William Kingdon Clifford                  | 1845 - 1879  |
| 56  | Gottlob Frege                             | 1848 - 1925  |
| 57  | Christian Felix Klein                     | 1849 - 1925  |
| 58  | Ferdinand Georg Frobenius                 | 1849 - 1917  |
| 59  | Sofya (Sonya) Kovalevskaya                | 1850 - 1891  |
| 60  | William Burnside                          | 1852 - 1927  |
| 61  | Jules Henri Poincaré                      | 1854 - 1912  |
| 62  | Giuseppe Peano                            | 1858 - 1932  |
| 63  | David Hilbert                             | 1862 - 1943  |
| 64  | Hermann Minkowski                         | 1864 - 1909  |
| 65  | Jacques Hadamard                          | 1865 - 1963  |
| 66  | Ivar Fredholm                             | 1866 - 1927  |
| 67  | Charles-Jean de la Vallée Poussin         | 1866 - 1962  |
| 68  | Felix Hausdorff                           | 1868 - 1942  |
| 69  | Élie Joseph Cartan                        | 1869 - 1951  |
| 70  | Emile Borel                               | 1871 - 1956  |
| 71  | Bertrand Arthur William Russell           | 1872 - 1970  |
| 72  | Henri Lebesgue                            | 1875 - 1941  |
| 73  | Godfrey Harold Hardy                      | 1877 - 1947  |
| 74  | Frigyes (Frédéric) Riesz                  | 1880 - 1956  |
| 75  | Luitzen Egbertus Jan Brouwer              | 1881 - 1966  |
| 76  | Emmy Noether                              | 1882 - 1935  |
| 77  | Waclaw Sierpiński                         | 1882 - 1969  |
| 78  | George Birkhoff                           | 1884 - 1944  |
| 79  | John Edensor Littlewood                   | 1885 - 1977  |
| 80  | Hermann Weyl                              | 1885 - 1955  |
| 81  | Thoralf Skolem                            | 1887 - 1963  |
| 82  | Srinivasa Ramanujan                       | 1887 - 1920  |
| 83  | Richard Courant                           | 1888 - 1972  |
| 84  | Stefan Banach                             | 1892 - 1945  |
| 85  | Norbert Wiener                            | 1894 - 1964  |
| 86  | Emil Artin                                | 1898 - 1962  |
| 87  | Alfred Tarski                             | 1901 - 1983  |
| 88  | Andrej Nicolaevich Kolmogorov             | 1903 - 1987  |
| 89  | Alonzo Church                             | 1903 - 1995  |
| 90  | William Vallance Douglas Hodge            | 1903 - 1975  |
| 91  | John von Neumann                          | 1903 - 1957  |
| 92  | Kurt Gödel                                | 1906 - 1978  |
| 93  | André Weil                                | 1906 - 1998  |
| 94  | Alan Turing                               | 1912 - 1954  |
| 95  | Abraham Robinson                          | 1918 - 1974  |
| 96  | Nicolas Bourbaki                          | 1935 -       |
|     |                                           |              |
I wrote a Python program to scrape the Wikipedia pages of these mathematicians, and asked for 3 measures:
- **PageRank**: a recursive measure: a node is important if it's linked to by other important nodes, not just by many nodes. It captures a kind of "endorsement quality" - being cited by Euler counts for more than being cited by an obscure footnote, which makes it a natural correction to in-degree's blind spot.
- **Indegree**: the number of incoming edges a node receives — here, how many other mathematicians cite, build on, or reference a given one. It's the simplest measure of raw popularity or recognition, but it treats every incoming link as equal, regardless of who's giving it.
- **Betweenness**; measures how often a node sits on the shortest path between other pairs of nodes - it's a measure of brokerage, not popularity. A mathematician with high betweenness may not be the most cited, but they're the bridge connecting otherwise-separate schools of thought. 
**A note on methodology.** Before diving into the results, one clarification matters: these rankings are computed on the subgraph formed by the 96 mathematicians only, not on the full Wikipedia link graph. So when I say "Abel beats Euler," I mean: within this curated list, the network structure concentrates relatively more influence on Abel — not that Abel outranks Euler across all of Wikipedia. That's still a meaningful finding, but it's a narrower one, and worth stating plainly.

The graph is directed, built from name mentions across these mathematicians' Wikipedia pages, and PageRank was computed with the standard damping factor of 0.85.

The outcome was sometimes as expected, sometimes surprising. Below is a table with the main result. Giving all 96 would be overload:
### Top 20 Most Influential Mathematicians (Within This Network of 96)

| PR Rank | Mathematician                    | PageRank | InDegree | ID Rank | Betweenness | BW Rank |
| ------- | -------------------------------- | -------- | -------- | ------- | ----------- | ------- |
| 1       | Niels Henrik Abel                | 0.03905  | 0.30526  | 5       | 0.04869     | 7       |
| 2       | Carl Friedrich Gauss             | 0.03831  | 0.33684  | 1       | 0.10914     | 2       |
| 3       | Isaac Newton                     | 0.03420  | 0.30526  | 5       | 0.04432     | 9       |
| 4       | Euclid                           | 0.03405  | 0.32632  | 2       | 0.03293     | 13      |
| 5       | Leonhard Euler                   | 0.03376  | 0.30526  | 5       | 0.06979     | 5       |
| 6       | David Hilbert                    | 0.03192  | 0.31579  | 3       | 0.11249     | 1       |
| 7       | Gottfried Wilhelm Leibniz        | 0.02494  | 0.21053  | 9       | 0.07558     | 3       |
| 8       | Joseph Louis Lagrange            | 0.02359  | 0.20000  | 11      | 0.02576     | 20      |
| 9       | Georg Friedrich Bernhard Riemann | 0.02222  | 0.28421  | 7       | 0.07345     | 4       |
| 10      | Augustin-Louis Cauchy            | 0.02208  | 0.21053  | 9       | 0.02035     | 25      |
| 11      | Pierre Fermat                    | 0.02194  | 0.16842  | 17      | 0.03781     | 10      |
| 12      | Pierre-Simon Laplace             | 0.02058  | 0.16842  | 17      | 0.01714     | 28      |
| 13      | Carl Gustav Jacob Jacobi         | 0.01947  | 0.20000  | 11      | 0.01466     | 31      |
| 14      | Apollonius                       | 0.01868  | 0.08421  | 40      | 0.01779     | 27      |
| 15      | Georg Cantor                     | 0.01815  | 0.18947  | 14      | 0.05613     | 6       |
| 16      | Jean Baptiste Joseph Fourier     | 0.01809  | 0.22105  | 8       | 0.01077     | 38      |
| 17      | Archimedes                       | 0.01799  | 0.09474  | 33      | 0.00788     | 49      |
| 18      | René Descartes                   | 0.01753  | 0.11579  | 27      | 0.02615     | 19      |
| 19      | Bertrand Arthur William Russell  | 0.01592  | 0.16842  | 17      | 0.02740     | 17      |
| 20      | Jules Henri Poincaré             | 0.01588  | 0.18947  | 14      | 0.03529     | 11      |
### Key Findings

The network analysis reveals several surprising insights:

**Abel beats Euler - within this network.** Contrary to the popular belief that Euler dominated mathematics, Niels Henrik Abel ranks #1 in PageRank influence among these 96, followed by Gauss and Newton. Euler, while still among the elite, ranks #5 — suggesting that within this particular set of peers, his influence is more distributed than concentrated, rather than uniquely dominant.

**Different metrics tell different stories.** Gauss dominates in citation count (InDegree rank #1), making him the most directly referenced mathematician in this set. But David Hilbert, ranked only #6 in PageRank, achieves the highest Betweenness centrality (#1), meaning he serves as the crucial bridge connecting different mathematical traditions and schools of thought - a role that raw popularity metrics miss entirely.

**Ancient mathematics endures.** Euclid (#4), Archimedes (#17), and Apollonius (#14) still rank among the top influences despite living over 2,000 years ago. This suggests that foundational, geometric thinking remains essential to modern mathematics.

**Influence is not monolithic.** The variation in rankings across the three metrics shows that influence operates on different levels: raw citation count, network centrality, and bridge-building. A mathematician might be widely cited (high InDegree) but not central to connecting fields (low Betweenness), or vice versa - a reminder that "who mattered most" depends entirely on which kind of mattering you measure.

What strikes me most, though, isn't really about mathematicians. It's a pattern I recognize from 25 years in ERP consulting: success gets attributed to a single genius, a single hero-consultant, a single "who saved the project." But the network — much like Hilbert's high betweenness despite a lower PageRank — usually tells a different story. The bridge-builders, the ones connecting disconnected parts of a system, rarely get the credit that the most-cited or most-visible node does. Whether it's mathematical influence or an ERP implementation, the myth of the lone genius tends to obscure the structure that actually did the work.

I made an interactive graph representation of the Wikipedia links:

[View interactive network visualization](Results/mathematicians_network_stable.html)