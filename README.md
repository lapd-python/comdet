comdet
======
In the study of complex networks, a network is said to have community structure if the nodes of the network can be easily grouped into (potentially overlapping) sets of nodes such that each set of nodes is densely connected internally.

comdet is used to detect community among graph nodes. Its based on lovain method


Installation
-------------
Easy install
```shell
easy_install comdet
````

Pip:
```shell
$pip install comdet
```

or just download the package from here and use it as stand alone.

Usage
-------------

from comdet import comdet
result = comdet.detect("input", debug=True)
print result

####Input file

Input files  contains space separated src dst pair of graph nodes
eg.
```shell
DL0 DL4
DL3 DL6
DL8 DL2
DL4 DL3
DL2 DL2
DL3 DL4
DL2 DL8
DL8 DL4
DL0 DL7
DL10 DL4
DL9 DL6
DL8 DL6
DL2 DL8
DL9 DL10
DL8 DL8
DL4 DL9
.
.
.
```
####Output

Output is nested list of community structure.
```shell
[[[[['DL23', 'DL19', 'DL27']], [['DL28', 'DL26', 'DL20'], ['DL44'], ['DL38', 'DL46', 'DL42'], ['DL10', 'DL6', 'DL1', 'DL2', 'DL0'], ['DL34', 'DL37']]]]]
```
```
The above output consist of 4 passes.
Pass 1 => 
1Group1 - ['DL23', 'DL19', 'DL27']]
1Group2 - ['DL28', 'DL26', 'DL20']
1Group3 - ['DL44']
1Group4 - ['DL10', 'DL6', 'DL1', 'DL2', 'DL0']
1Group5 - ['DL34', 'DL37']

Pass2  => 
Now nodes of previous pass group together to form mode strong community.
2Group1 - [1Group1]
2Group2 - [1Group2, 1Group3, 1Group4, 1Group5]

Pass3  =>
3Group1 - [2Group1, 2Group3]

Pass4 => 
4Group1 - [3Group1]

Pass5 => 
5Group1 - [4Group1]
Now as the number of community in pass4 and Pass5 are same the processing stops and pass 4 output is taken.
```
