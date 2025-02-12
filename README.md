## GULP-GAP interface 
version 2.0.2
This is NOT the usage version. If you want the detail and the geunine scripts please contact me.
tonggih.kang.18@ucl.ac.uk

✅ Aug 2022: v1.0.0 preparing trainig data using GULP<br>
✅ Aug 2022: v1.1.0 GAP training<br>
✅ Sep 2022: v1.2.0 dimer curve (Al-F pairwise interaction energy vs interatomic distance)<br>
✅ Oct 2022: v1.3.0 separate the prep, train, vis scripts<br>
✅ Oct 2022: v1.3.1 vis script: RDF<br>
✅ Nov 2022: v1.3.2 vis script: histogram instead of RDF<br>
✅ Dec 2022: v1.4.0 prep: degeracy filter<br>
✅ Dec 2022: v1.4.1 prep: symmetric (duplicate) configuration filter<br>
✅ Dec 2022: v1.4.2 prep: extremely short interatomic dist filter [degeneracyFilter branch]<br>

✅ Jan 2023: v2.0.0 Further modulised scripts (version 2)<br>
✅ Feb 2023: v2.0.1 Stochastic approach of atomic position displacement, (removed: poor degeneracy filter, energy filter)<br>
(at the moment you have to manually turn-on/off the stochastic function)<br>
✅ Mar 2023: v2.0.2 Automatically take average bond distance of cation-cation and anion-anion for RMSE calculation in the ±0.5 angstrom region and plot vertical line at the average bond distance
* * *
[linke to the image](https://github.com/DGKang234/ML_POT/blob/degeneracyFilter/parameter_search/htmls)
![alt text](https://github.com/DGKang234/ML_POT/blob/degeneracyFilter/parameter_search/htmls/GAP_r-cutoff-energy.png)
![alt text](https://github.com/DGKang234/ML_POT/blob/degeneracyFilter/parameter_search/htmls/GAP_sparse-cutoff-energy_F-F.png)

* * *
How to use the code: <br>
```python GULP_GAP.py '{eigvec 1} {eigvec 2}...{eigvec n}' {step size for the lambda} {from what IP rank structure} {to what IP rank structure} {n or y (whether including the breathing config or not)} {GAP cutoff parameter} {GAP n_sparce parameter} {degeneracy/duplicate filter}```
<br>
**Example**: ```python GULP_GAP.py '7 9 12' 10 1 10 n 3.0 100 y```

```first_GAP.py```<br>
Preparing IP structures (IP optimised structures, breathing configurations, IP optimised structures + (eigenvector*λ). <br>
It will consider degenerate frequencies to select only one frequency which is to avoid the overfitting the potential energy landscape. <br>
(It will select first frequency among the degenerate frequencies for the training. For example, 7 and 8 are degenerate, then it will use 7th frequency(eigenvalue/eigenvector))
<br>
***N.B.*** At the moment 100 % of dataset will be distributed as a training dataset if you want to distribute some to validation/test set please change from **line 133**.

```second_GAP.py```<br>
Fitting the GAP potential on the prepared GULP training data

```third.py```<br>
Visualise the potential from QUIP output using ```plotly```; potential energy VS interatomic potential
(it shows the ideal potentials that we want to reproduce, GAP potentials (cation-anion and anion-anion), RDF of the training data configurations, transparent-boxed interatomic distance region (green/red) that covered by the training data (cation-anion/anion-anion) 

<br>
<br>
*The script will be further modulised for numerous purpose. If you have any questions about the project please ask me*
