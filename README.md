# IsingProblem
Code for Math Senior Seminar Capstone

# Project Outline:

Goal: Create a program to solve the ising model on any three-regular graph?

Equations:  
                       V = vertex set  
                       E = edge set  
                       |V| = # Vertices  
                       |E| = # Edges  
                       a = microstate  
                       H_a = Hamiltonian of a microstate  
                       P_a = probability of a microstate  
                       Z = partition function  
                       k_B = boltzmann's constant (can be 1)  
                       T = temperature  
                       M_a = total magnetization of a microstate  
                       m = expectation value of all microstates  


                       |V| = 3 * 2^n - 2
                       |E| = 9 * 2^(n-1) - 3 = 3/2 |V|

                        H_a = - J * (sum over all edges i, j) spin_i * spin_j,   J > 0
                        P_a = (1 / Z) exp[- (1/k_B * T) * H_a]
                        Z = (sum over all microstates) exp[- (1/k_B * T) * H_a]
                        M_a = (sum over vertices) spin_v
                        m = (sum over all microstates) M_a * P_a

# Implementation
Data Structures:  
Should make a representation for vertices and edges  
for easy operation, maybe have microstate be denoted by number 0 -> (2^N) - 1. Put this into a list removing 0b prefix, and then can transform by 0 = -1.
Could represent vertices as a list V (integer V_i), i = 0 -> N - 1, V_i = +/- 1  
edges, list E (integer E1_j, integer E2_k), j,k = indexes of adjacent V  
would need easy way to generate list of edges, maybe can have it read from a file   
microstates, list A (double A_x) x = 0 -> (2^N) - 1, A_x = H_x  
Z global variable  

Methods:  
need to initialize vertice list to microstate  
initializer for edge set?  
H_a -> iterate over all elements in edge set, doing eq; should be called once, fill microstates array (doubles for accuracy)  
Z -> iterate over all A_x; should be called once for each configuration of edges; double for accuracy  
P_a -> abstraction method for readability; called many times within m  
M_a -> iterate over vertices; called within m  
m -> iterate over all microstates;   

# things to consider
Does the graph have to be hamiltonian (probably?)  
does the girth of a graph matter?
