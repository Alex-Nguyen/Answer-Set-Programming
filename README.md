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
    #number =1..9.
    #div = 0..8.
predicates
    %square(X,Y,N) denotes that the value of square at row X, column Y is N
    square(#index, #index, #number).
    %div(X,N) denotes that the number of divides in long division X by 3 is N. Example, {0,1,2} div 3 = 0, {3,4,5} div 3 = 1, {6,7,8} div 3 = 2.
    div(#index, #div).
rules
    %Ininitially, all squares have all possible values from 1 to 9.
    square(X,Y,1) | square(X,Y,2) | square(X,Y,3)| square(X,Y,4)| square(X,Y,5)| square(X,Y,6)| square(X,Y,7)| square(X,Y,8)| square(X,Y,9).
    
    %Narrow down the search space with values
    square(0,0,6).
    square(0,4,5).
    square(0,8,3).
    
    square(1,1,5).
    square(1,3,7).
    square(1,6,6).
    
    square(2,0,8).
    square(2,3,4).
    square(2,6,1).
    square(2,7,7).
    
    square(3,0,5).
    square(3,3,2).
    square(3,4,1).
    square(3,6,9).
    
    square(4,3,6).
    square(4,5,9).
    
    square(5,2,6).
    square(5,4,8).
    square(5,5,3).
    square(5,8,1).
    
    square(6,1,8).
    square(6,2,5).
    square(6,5,7).
    square(6,8,2).
    
    square(7,2,3).
    square(7,5,6).
    square(7,7,5).
    
    square(8,0,2).
    square(8,4,9).
    square(8,8,7).
    
    %Define div rule
    div(X, N):-X/3 = N.
    
    % Numbers of the same row X can not have the same value N. 
    :-square(X,Y1, N), square(X,Y2,N), Y1!=Y2.
    
     % Numbers of the same column Y can not have the same value N. 
    :-square(X1,Y, N), square(X2,Y,N), X1!=X2.
    
    % Numbers of the same block can not have the same value N. 
    :-square(X1,Y1,N), square(X2,Y2,N), div(X1,N1), div(X2,N1), div(Y1,N1), div(Y2,N1), X1 !=X2, Y1!=Y2.
```
