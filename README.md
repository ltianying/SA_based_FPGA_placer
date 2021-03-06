# SA based FPGA placer
The implementation of a simulated annealing based standard-cell placement tool.

### Objective
![floorplan](https://user-images.githubusercontent.com/15523357/28557837-9f456f8e-70c3-11e7-8dcc-da1d90a1557b.png)

Each space which can be occupied by a cell is referred as a cell site. There are nx sites and ny rows. The problem is to design a tool to place each cell of a circuit on the floor-plan while following any given design rules, which are discussed in the next section.

### Design Rules
* All the cells in a circuit are squares and have the same size(same height and width).
* We cannot assign more than one cell to each site/space on the floor-plan.
* The routing channel is of the same height as a row of cells.
* The distance between two cells is measured from the center of one cell to the center of the other.
* No extra artificial penalties are given for a net which crosses a row.
* The product of nx* ny should be at least as large as the number of cells in the circuit.

### Requirements
In order to run the program, the user is required to have the following modules installed:
* Python 3.x
* Matplotlib
* Numpy

### Pseudocode
The basic pseudocode for the placement tool is given below:
```
1: select circuit
2: set initial placement
3: set initial temperature and iterations
4: While not exit condition do
5:    For k iterations do
6:        select cells to swap
7.            Calculate new cost
8.            Calculate deltaC = New cost - Old cost
9.        if(deltaC <0)
10.           Accept the solution
11.       Else:
12.           R = rand(0,1)
13.           if(R< e−deltaC/T )then
14.               Accept the solution
16.           Else
17.               Reject solution
18.       End if
19.   End for
20.   Update T
21.   Update net criticality
22.End while
```
### License

MIT License

Copyright (c) 2018 Jaspreet Jhoja

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
