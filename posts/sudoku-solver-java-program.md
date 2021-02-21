---
title: Java Program to solve Sudoku
created: 2016-10-19T02:20:57+05:30
author: ashishdoneriya
description: java program to solve Sudoku problems, based on Depth First Search.
permalink: /sudoku-solver-java-program.html
tags:
  - java
updated: 2016-10-19T02:20:57+05:30
categories:
  - java
---

This program is based on Depth First Search or Back track Algorithm.

```java
package com.csetutorials;

import java.util.Arrays;
import java.util.Scanner;
import java.util.Set;
import java.util.TreeSet;

public class Sudoku {

  public static void main(String[] args) {
    Sudoku sudoku = new Sudoku();

    // Creating a sudoku board
    int[][] board = new int[][] {
        { 0, 0, 0, 0, 0, 6, 0, 0, 0 },
        { 0, 2, 7, 5, 1, 0, 9, 0, 8 },
        { 3, 9, 0, 7, 0, 0, 0, 0, 5 },
        { 0, 1, 0, 0, 0, 0, 0, 0, 0 },
        { 9, 0, 4, 0, 0, 0, 3, 0, 6 },
        { 0, 0, 0, 0, 0, 0, 0, 4, 0 },
        { 5, 0, 0, 0, 0, 7, 0, 9, 4 },
        { 8, 0, 1, 0, 6, 5, 2, 3, 0 },
        { 0, 0, 0, 4, 0, 0, 0, 0, 0 } };
    int[][] result = sudoku.getResult(board);

    // Printing the final result
    sudoku.printSudoku(result);
  }

  public int[][] getResult(int[][] board) {
    int row, column;
    Set&lt;Integer> possibleValuesList;
    for (row = 0; row &lt; 9; row++) {
      for (column = 0; column &lt; 9; column++) {
        if (board[row][column] != 0) {
          continue;
        }
        // Getting possible values that can be
        // filled at position [row, column]
        possibleValuesList = getPossibleValues(row,
            column, board);

        // If there are no such values that can be
        // filled then return to its parent so that
        // its parent could return to its parent or
        // pass another possible value to child (recursion)
        if (possibleValuesList.size() == 0) {
          return null;
        } else {
          for(int possibleValue:possibleValuesList){

            // Identical sudoku but its filled with
            // a possible value
            int[][] copy = getCopy(row, column,
                possibleValue, board);

            // Recursion
            int[][] result = getResult(copy);
            if (result != null) {
              return result;
            }
          }
          // If non of the posible values could give
          // answer then return to its parent
          return null;
        }
      }
    }

    // Returning final result
    return board;
  }

  // Create a clone of existing sudoku and fill the
  // num at [row, column]
  public int[][] getCopy(int row, int column, int num,
      int[][] board) {
    int[][] board_copy = new int[board.length][];
    for (int i = 0; i &lt; board.length; i++) {
      board_copy[i] = board[i].clone();
    }
    board_copy[row][column] = num;
    return board_copy;
  }

  // Returns the list of values that can be filled
  // at [row, column]
  public Set&lt;Integer> getPossibleValues(int row,
      int column, int[][] board) {
    int i, j;
    Set&lt;Integer> canNotBeAdded = new TreeSet&lt;Integer>();

    // Get already filled horizontal elements
    for (i = 0; i &lt; 9; i++) {
      canNotBeAdded.add(board[row][i]);
    }

    // Get already filled vertical elements
    for (i = 0; i &lt; 9; i++) {
      canNotBeAdded.add(board[i][column]);
    }

    // Get all elements which are in the same box
    // as the point/number [row, column]
    int boxRowStart = row - row % 3,
        boxColumnStart = column - column % 3;
    for (i = boxRowStart; i &lt; boxRowStart + 3; i++) {
      for (j = boxColumnStart; j &lt; boxColumnStart + 3; j++) {
        canNotBeAdded.add(board[i][j]);
      }
    }

    Set&lt;Integer> canBeAdded = new TreeSet&lt;Integer>();
    for (i = 1; i &lt;= 9; i++) {
      canBeAdded.add(i);
    }
    canBeAdded.removeAll(canNotBeAdded);
    return canBeAdded;
  }

  // Printing sudoku
  private void printSudoku(int[][] board) {
    System.out.println("Printing Result");
    int row, column;
    for (row = 0; row &lt; 9; row++) {
      for (column = 0; column &lt; 9; column++) {
        System.out.print(board[row][column] + " ");
      }
      System.out.println();
    }
  }

  // Takes the input from user and returns the board
  public int[][] getInputFromUser() {
    int[][] board = new int[9][9];
    Scanner kb = new Scanner(System.in);
    int row, column;
    for (row = 0; row &lt; 9; row++) {
      for (column = 0; column &lt; 9; column++) {
        board[row][column] = kb.nextInt();
      }
    }
    kb.close();
    return board;
  }
}
```


Using this algorithm I have created sudoku solver on <a href="https://ashishdoneriya.github.io/sudoku/" rel="noopener" target="_blank">github</a>.
