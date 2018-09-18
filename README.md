# Answer-Set-Programming
This repository contains all materials on Answer set programming
## Sudoku 
The Rules of Sudoku
The classic Sudoku game involves a grid of 81 squares. The grid is divided into nine blocks, each containing nine squares.

The rules of the game are simple: each of the nine blocks has to contain all the numbers 1-9 within its squares. Each number can only appear once in a row, column or box.
![alt text](https://github.com/Alex-Nguyen/Answer-Set-Programming/blob/master/sudoku.PNG)

```
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%% Template for a SPARC file
%% Author: Vinh Nguyen (Texas Tech University)
%% Description: This example illustrates how to use Answer Set Programming to solve Sudoku problem
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

sorts
    #index =0..8.
    #mode_range = 0..8.
predicates
    square(#index, #index, #number).
    mode(#index, #mode_range).
rules
    square(X,Y,1) | square(X,Y,2) | square(X,Y,3)| square(X,Y,4)| square(X,Y,5)| square(X,Y,6)| square(X,Y,7)| square(X,Y,8)| square(X,Y,9).
    square(0,4,7).
    square(0,5,4).
    square(0,6,6).
    
    square(1,0,8).
    square(1,2,7).
    square(1,3,5).
    
    square(2,0,5).
    square(2,2,4).
    square(2,4,9).
    square(2,7,2).
    
    square(3,0,4).
    square(3,1,1).
    square(3,5,5).
    square(3,8,2).
    
    square(4,2,8).
    square(4,3,1).
    square(4,4,2).
    square(4,5,3).
    square(4,6,4).
    
    square(5,0,9).
    square(5,1,2).
    square(5,3,8).
    square(5,7,3).
    square(5,8,1).
    
    square(6,6,2).
    square(6,7,6).
    square(6,8,4).
    
    square(7,1,7).
    square(7,2,2).
    square(7,6,3).
    square(7,7,8).
    
    square(8,0,3).
    
    mode(X, N):-X/3 = N.
    :-square(X,Y1, N), square(X,Y2,N), Y1!=Y2.
    :-square(X1,Y, N), square(X2,Y,N), X1!=X2.
    :-square(X1,Y1,N), square(X2,Y2,N), mode(X1,N1), mode(X2,N1), mode(Y1,N1), mode(Y2,N1), X1 !=X2, Y1!=Y2.
```
