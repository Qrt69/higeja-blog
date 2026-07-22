---
title: "Is Euler really the greatest?"
description: "A network analysis of 96 great mathematicians reveals that Euler, despite his reputation, isn't the most central figure — and the reason why says something about how we assign credit in general."
pubDate: 2026-07-19
draft: false
---

A few weeks ago, someone told me: "Everything in mathematics could eventually be named after Euler, because he was truly the greatest". First of all, I'm not a mathematician at all, so I'm not the person to argue about this. But I am truly interested in mathematics, especially when they are related to IT in general, and more specifically graph theory, data science and deep learning in particular. And already with this basic math knowledge, I have to admit that Euler was truly one of the greatest mathematicians of all time.

But: was he truly the greatest? Triggered by my interest for graph theory, I did a small experiment. I found a list of 96 mathematicians in "The Princeton Companion to Mathematics", a book by Timothy Gowers, University of Cambridge. Then I looked up these 96 mathematicians on Wikipedia, and wrote a program to count the number of links to the others. Doing so, I could make a ranking of the most central mathematicians within this network of 96 — not "of all time," but relative to each other, based purely on how their Wikipedia pages link together.

First of all, the list of mathematicians:

<table>
<tr><th>#</th><th>Name</th><th>Years</th></tr>
<tr><td>1</td><td>Pythagoras</td><td>ca. 569 B.C.</td></tr>
<tr><td>2</td><td>Euclid</td><td>ca. 325 B.C.</td></tr>
<tr><td>3</td><td>Archimedes</td><td>ca. 287 B.C.</td></tr>
<tr><td>4</td><td>Apollonius</td><td>ca. 262 B.C.</td></tr>
<tr><td>5</td><td>Abu Ja'far Muhammad ibn Mūsā al-Khwārizmī</td><td>800 - 847</td></tr>
<tr><td>6</td><td>Leonardo of Pisa (known as Fibonacci)</td><td>1170 - 1250</td></tr>
<tr><td>7</td><td>Girolamo Cardano</td><td>1501 - 1576</td></tr>
<tr><td>8</td><td>Rafael Bombelli</td><td>1526 - 1572</td></tr>
<tr><td>9</td><td>François Viète</td><td>1540 - 1603</td></tr>
<tr><td>10</td><td>Simon Stevin</td><td>1548 - 1620</td></tr>
<tr><td>11</td><td>René Descartes</td><td>1596 - 1650</td></tr>
<tr><td>12</td><td>Pierre Fermat</td><td>1600 - 1665</td></tr>
<tr><td>13</td><td>Blaise Pascal</td><td>1623 - 1662</td></tr>
<tr><td>14</td><td>Isaac Newton</td><td>1642 - 1727</td></tr>
<tr><td>15</td><td>Gottfried Wilhelm Leibniz</td><td>1646 - 1716</td></tr>
<tr><td>16</td><td>Brook Taylor</td><td>1685 - 1731</td></tr>
<tr><td>17</td><td>Christian Goldbach</td><td>1690 - 1764</td></tr>
<tr><td>18</td><td>The Bernoullis</td><td>—</td></tr>
<tr><td>19</td><td>Leonhard Euler</td><td>1707 - 1783</td></tr>
<tr><td>20</td><td>Jean Le Rond d'Alembert</td><td>1717 - 1783</td></tr>
<tr><td>21</td><td>Edward Waring</td><td>1735 - 1798</td></tr>
<tr><td>22</td><td>Joseph Louis Lagrange</td><td>1736 - 1813</td></tr>
<tr><td>23</td><td>Pierre-Simon Laplace</td><td>1749 - 1827</td></tr>
<tr><td>24</td><td>Adrien-Marie Legendre</td><td>1752 - 1833</td></tr>
<tr><td>25</td><td>Jean Baptiste Joseph Fourier</td><td>1768 - 1830</td></tr>
<tr><td>26</td><td>Carl Friedrich Gauss</td><td>1777 - 1855</td></tr>
<tr><td>27</td><td>Siméon-Denis Poisson</td><td>1781 - 1840</td></tr>
<tr><td>28</td><td>Bernard Bolzano</td><td>1781 - 1848</td></tr>
<tr><td>29</td><td>Augustin-Louis Cauchy</td><td>1789 - 1857</td></tr>
<tr><td>30</td><td>August Ferdinand Möbius</td><td>1790 - 1868</td></tr>
<tr><td>31</td><td>Nicolai Ivanovich Lobachevskii</td><td>1792 - 1856</td></tr>
<tr><td>32</td><td>George Green</td><td>1793 - 1841</td></tr>
<tr><td>33</td><td>Niels Henrik Abel</td><td>1802 - 1829</td></tr>
<tr><td>34</td><td>János Bolyai</td><td>1802 - 1860</td></tr>
<tr><td>35</td><td>Carl Gustav Jacob Jacobi</td><td>1804 - 1851</td></tr>
<tr><td>36</td><td>Peter Gustav Lejeune Dirichlet</td><td>1805 - 1859</td></tr>
<tr><td>37</td><td>William Rowan Hamilton</td><td>1805 - 1865</td></tr>
<tr><td>38</td><td>Augustus De Morgan</td><td>1806 - 1871</td></tr>
<tr><td>39</td><td>Joseph Liouville</td><td>1809 - 1882</td></tr>
<tr><td>40</td><td>Ernst Eduard Kummer</td><td>1810 - 1893</td></tr>
<tr><td>41</td><td>Évariste Galois</td><td>1811 - 1832</td></tr>
<tr><td>42</td><td>James Joseph Sylvester</td><td>1814 - 1897</td></tr>
<tr><td>43</td><td>George Boole</td><td>1815 - 1864</td></tr>
<tr><td>44</td><td>Karl Weierstrass</td><td>1815 - 1897</td></tr>
<tr><td>45</td><td>Pafnuty Chebyshev</td><td>1821 - 1894</td></tr>
<tr><td>46</td><td>Arthur Cayley</td><td>1821 - 1895</td></tr>
<tr><td>47</td><td>Charles Hermite</td><td>1822 - 1901</td></tr>
<tr><td>48</td><td>Leopold Kronecker</td><td>1823 - 1891</td></tr>
<tr><td>49</td><td>Georg Friedrich Bernhard Riemann</td><td>1826 - 1866</td></tr>
<tr><td>50</td><td>Julius Wilhelm Richard Dedekind</td><td>1831 - 1916</td></tr>
<tr><td>51</td><td>Émile Léonard Mathieu</td><td>1835 - 1890</td></tr>
<tr><td>52</td><td>Camille Jordan</td><td>1838 - 1922</td></tr>
<tr><td>53</td><td>Sophus Lie</td><td>1842 - 1899</td></tr>
<tr><td>54</td><td>Georg Cantor</td><td>1845 - 1918</td></tr>
<tr><td>55</td><td>William Kingdon Clifford</td><td>1845 - 1879</td></tr>
<tr><td>56</td><td>Gottlob Frege</td><td>1848 - 1925</td></tr>
<tr><td>57</td><td>Christian Felix Klein</td><td>1849 - 1925</td></tr>
<tr><td>58</td><td>Ferdinand Georg Frobenius</td><td>1849 - 1917</td></tr>
<tr><td>59</td><td>Sofya (Sonya) Kovalevskaya</td><td>1850 - 1891</td></tr>
<tr><td>60</td><td>William Burnside</td><td>1852 - 1927</td></tr>
<tr><td>61</td><td>Jules Henri Poincaré</td><td>1854 - 1912</td></tr>
<tr><td>62</td><td>Giuseppe Peano</td><td>1858 - 1932</td></tr>
<tr><td>63</td><td>David Hilbert</td><td>1862 - 1943</td></tr>
<tr><td>64</td><td>Hermann Minkowski</td><td>1864 - 1909</td></tr>
<tr><td>65</td><td>Jacques Hadamard</td><td>1865 - 1963</td></tr>
<tr><td>66</td><td>Ivar Fredholm</td><td>1866 - 1927</td></tr>
<tr><td>67</td><td>Charles-Jean de la Vallée Poussin</td><td>1866 - 1962</td></tr>
<tr><td>68</td><td>Felix Hausdorff</td><td>1868 - 1942</td></tr>
<tr><td>69</td><td>Élie Joseph Cartan</td><td>1869 - 1951</td></tr>
<tr><td>70</td><td>Emile Borel</td><td>1871 - 1956</td></tr>
<tr><td>71</td><td>Bertrand Arthur William Russell</td><td>1872 - 1970</td></tr>
<tr><td>72</td><td>Henri Lebesgue</td><td>1875 - 1941</td></tr>
<tr><td>73</td><td>Godfrey Harold Hardy</td><td>1877 - 1947</td></tr>
<tr><td>74</td><td>Frigyes (Frédéric) Riesz</td><td>1880 - 1956</td></tr>
<tr><td>75</td><td>Luitzen Egbertus Jan Brouwer</td><td>1881 - 1966</td></tr>
<tr><td>76</td><td>Emmy Noether</td><td>1882 - 1935</td></tr>
<tr><td>77</td><td>Waclaw Sierpiński</td><td>1882 - 1969</td></tr>
<tr><td>78</td><td>George Birkhoff</td><td>1884 - 1944</td></tr>
<tr><td>79</td><td>John Edensor Littlewood</td><td>1885 - 1977</td></tr>
<tr><td>80</td><td>Hermann Weyl</td><td>1885 - 1955</td></tr>
<tr><td>81</td><td>Thoralf Skolem</td><td>1887 - 1963</td></tr>
<tr><td>82</td><td>Srinivasa Ramanujan</td><td>1887 - 1920</td></tr>
<tr><td>83</td><td>Richard Courant</td><td>1888 - 1972</td></tr>
<tr><td>84</td><td>Stefan Banach</td><td>1892 - 1945</td></tr>
<tr><td>85</td><td>Norbert Wiener</td><td>1894 - 1964</td></tr>
<tr><td>86</td><td>Emil Artin</td><td>1898 - 1962</td></tr>
<tr><td>87</td><td>Alfred Tarski</td><td>1901 - 1983</td></tr>
<tr><td>88</td><td>Andrej Nicolaevich Kolmogorov</td><td>1903 - 1987</td></tr>
<tr><td>89</td><td>Alonzo Church</td><td>1903 - 1995</td></tr>
<tr><td>90</td><td>William Vallance Douglas Hodge</td><td>1903 - 1975</td></tr>
<tr><td>91</td><td>John von Neumann</td><td>1903 - 1957</td></tr>
<tr><td>92</td><td>Kurt Gödel</td><td>1906 - 1978</td></tr>
<tr><td>93</td><td>André Weil</td><td>1906 - 1998</td></tr>
<tr><td>94</td><td>Alan Turing</td><td>1912 - 1954</td></tr>
<tr><td>95</td><td>Abraham Robinson</td><td>1918 - 1974</td></tr>
<tr><td>96</td><td>Nicolas Bourbaki</td><td>1935 -</td></tr>
</table>

I wrote a Python program to scrape the Wikipedia pages of these mathematicians, and asked for 3 measures:

- **PageRank**: a recursive measure: a node is important if it's linked to by other important nodes, not just by many nodes. It captures a kind of "endorsement quality" — being cited by Euler counts for more than being cited by an obscure footnote, which makes it a natural correction to in-degree's blind spot.
- **Indegree**: the number of incoming edges a node receives — here, how many other mathematicians cite, build on, or reference a given one. It's the simplest measure of raw popularity or recognition, but it treats every incoming link as equal, regardless of who's giving it.
- **Betweenness**: measures how often a node sits on the shortest path between other pairs of nodes — it's a measure of brokerage, not popularity. A mathematician with high betweenness may not be the most cited, but they're the bridge connecting otherwise-separate schools of thought.

**A note on methodology.** Before diving into the results, one clarification matters: these rankings are computed on the subgraph formed by the 96 mathematicians only, not on the full Wikipedia link graph. So when I say "Abel beats Euler," I mean: within this curated list, the network structure concentrates relatively more influence on Abel — not that Abel outranks Euler across all of Wikipedia. That's still a meaningful finding, but it's a narrower one, and worth stating plainly.

The graph is directed, built from name mentions across these mathematicians' Wikipedia pages, and PageRank was computed with the standard damping factor of 0.85.

The outcome was sometimes as expected, sometimes surprising. Below is a table with the main result. Giving all 96 would be overload:

### Top 20 Most Influential Mathematicians (Within This Network of 96)

<table>
<tr><th>PR Rank</th><th>Mathematician</th><th>PageRank</th><th>InDegree</th><th>ID Rank</th><th>Betweenness</th><th>BW Rank</th></tr>
<tr><td>1</td><td>Niels Henrik Abel</td><td>0.03905</td><td>0.30526</td><td>5</td><td>0.04869</td><td>7</td></tr>
<tr><td>2</td><td>Carl Friedrich Gauss</td><td>0.03831</td><td>0.33684</td><td>1</td><td>0.10914</td><td>2</td></tr>
<tr><td>3</td><td>Isaac Newton</td><td>0.03420</td><td>0.30526</td><td>5</td><td>0.04432</td><td>9</td></tr>
<tr><td>4</td><td>Euclid</td><td>0.03405</td><td>0.32632</td><td>2</td><td>0.03293</td><td>13</td></tr>
<tr><td>5</td><td>Leonhard Euler</td><td>0.03376</td><td>0.30526</td><td>5</td><td>0.06979</td><td>5</td></tr>
<tr><td>6</td><td>David Hilbert</td><td>0.03192</td><td>0.31579</td><td>3</td><td>0.11249</td><td>1</td></tr>
<tr><td>7</td><td>Gottfried Wilhelm Leibniz</td><td>0.02494</td><td>0.21053</td><td>9</td><td>0.07558</td><td>3</td></tr>
<tr><td>8</td><td>Joseph Louis Lagrange</td><td>0.02359</td><td>0.20000</td><td>11</td><td>0.02576</td><td>20</td></tr>
<tr><td>9</td><td>Georg Friedrich Bernhard Riemann</td><td>0.02222</td><td>0.28421</td><td>7</td><td>0.07345</td><td>4</td></tr>
<tr><td>10</td><td>Augustin-Louis Cauchy</td><td>0.02208</td><td>0.21053</td><td>9</td><td>0.02035</td><td>25</td></tr>
<tr><td>11</td><td>Pierre Fermat</td><td>0.02194</td><td>0.16842</td><td>17</td><td>0.03781</td><td>10</td></tr>
<tr><td>12</td><td>Pierre-Simon Laplace</td><td>0.02058</td><td>0.16842</td><td>17</td><td>0.01714</td><td>28</td></tr>
<tr><td>13</td><td>Carl Gustav Jacob Jacobi</td><td>0.01947</td><td>0.20000</td><td>11</td><td>0.01466</td><td>31</td></tr>
<tr><td>14</td><td>Apollonius</td><td>0.01868</td><td>0.08421</td><td>40</td><td>0.01779</td><td>27</td></tr>
<tr><td>15</td><td>Georg Cantor</td><td>0.01815</td><td>0.18947</td><td>14</td><td>0.05613</td><td>6</td></tr>
<tr><td>16</td><td>Jean Baptiste Joseph Fourier</td><td>0.01809</td><td>0.22105</td><td>8</td><td>0.01077</td><td>38</td></tr>
<tr><td>17</td><td>Archimedes</td><td>0.01799</td><td>0.09474</td><td>33</td><td>0.00788</td><td>49</td></tr>
<tr><td>18</td><td>René Descartes</td><td>0.01753</td><td>0.11579</td><td>27</td><td>0.02615</td><td>19</td></tr>
<tr><td>19</td><td>Bertrand Arthur William Russell</td><td>0.01592</td><td>0.16842</td><td>17</td><td>0.02740</td><td>17</td></tr>
<tr><td>20</td><td>Jules Henri Poincaré</td><td>0.01588</td><td>0.18947</td><td>14</td><td>0.03529</td><td>11</td></tr>
</table>

### Key Findings

The network analysis reveals several surprising insights:

**Abel beats Euler — within this network.** Contrary to the popular belief that Euler dominated mathematics, Niels Henrik Abel ranks #1 in PageRank influence among these 96, followed by Gauss and Newton. Euler, while still among the elite, ranks #5 — suggesting that within this particular set of peers, his influence is more distributed than concentrated, rather than uniquely dominant.

**Different metrics tell different stories.** Gauss dominates in citation count (InDegree rank #1), making him the most directly referenced mathematician in this set. But David Hilbert, ranked only #6 in PageRank, achieves the highest Betweenness centrality (#1), meaning he serves as the crucial bridge connecting different mathematical traditions and schools of thought — a role that raw popularity metrics miss entirely.

**Ancient mathematics endures.** Euclid (#4), Archimedes (#17), and Apollonius (#14) still rank among the top influences despite living over 2,000 years ago. This suggests that foundational, geometric thinking remains essential to modern mathematics.

**Influence is not monolithic.** The variation in rankings across the three metrics shows that influence operates on different levels: raw citation count, network centrality, and bridge-building. A mathematician might be widely cited (high InDegree) but not central to connecting fields (low Betweenness), or vice versa — a reminder that "who mattered most" depends entirely on which kind of mattering you measure.

What strikes me most, though, isn't really about mathematicians. It's a pattern I recognize from 25 years in ERP consulting: success gets attributed to a single genius, a single hero-consultant, a single "who saved the project." But the network — much like Hilbert's high betweenness despite a lower PageRank — usually tells a different story. The bridge-builders, the ones connecting disconnected parts of a system, rarely get the credit that the most-cited or most-visible node does. Whether it's mathematical influence or an ERP implementation, the myth of the lone genius tends to obscure the structure that actually did the work.

[View the interactive network visualization](/network/mathematicians-network.html)
