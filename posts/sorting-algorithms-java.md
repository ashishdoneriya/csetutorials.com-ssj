---
title: Sorting Algorithms implementation in Java
created: 2021-03-07T09:08:31+05:30
author: ashishdoneriya
description: Various sorting algorithms that I have implemented in Java
permalink: /sorting-algorithms-in-java.html
updated: 2021-03-07T09:08:31+05:30
categories:
  - java
tags:
  - java
  - algorithms
---

## Algorithms - 
1. [Quick Sort](#quick-sort)
2. [Selection Sort](#selection-sort)

### Quick Sort

In quick sort we choose first or last element in array as pivot element and categorize the elements based on whether they are smaller or greater than the pivot element.

```java
public class QuickSort {

	public static void main(String[] args) {
		int[] arr = new int[] 
			{ 4, 1, 4, 6, 21, 3, 7, 2, 5, 67, 52, 3, 23, 6, 2, 2 };
		quickSort(arr, 0, arr.length - 1);
		for (int num : arr) {
			System.out.print(num + " ");
		}
	}

	private static void quickSort(int[] arr, int low, int high) {
		if (high <= low) {
			return;
		}
		int pivotIndex = getPivotIndex(arr, low, high);

		quickSort(arr, low, pivotIndex - 1);
		quickSort(arr, pivotIndex + 1, high);
	}

	private static int getPivotIndex(int[] arr, int low, int high) {
		if (low >= high) {
			return low;
		}
		int pivot = arr[low];
		int i = low + 1;
		int j = high;

		while (i < j && i > 0 && j > 0 
			&& i < arr.length && j < arr.length) {

			while (pivot >= arr[i] && i < j) {
				i++;
			}
			while (pivot < arr[j] && i <= j) {
				j--;
			}
			if (i < j) {
				swap(arr, i, j);
			}

		}

		swap(arr, j, low);
		return j;
	}

	private static void swap(int[] arr, int i, int j) {
		int temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
	}
}
```


### Selection Sort

In selection sort we find the minimum number in the array and put it at the starting of array.

```java
public class SelectionSort {

	public static void main(String[] args) {
		int[] arr = new int[] 
			{ 4, 1, 4, 6, 21, 3, 7, 2, 5, 67, 52, 3, 23, 6, 2, 2 };
		sort(arr);
		print(arr);
	}

	public static void sort(int[] arr) {
		for (int i = 0; i < arr.length - 1; i++) {
			int minNumIndex = getMinNumIndex(arr, i);
			swap(arr, i, minNumIndex);
		}
	}

	private static int getMinNumIndex(int[] arr, int startingIndex) {
		int minNumIndex = startingIndex;
		for (int i = minNumIndex + 1; i < arr.length; i++) {
			if (arr[minNumIndex] > arr[i]) {
				minNumIndex = i;
			}
		}
		return minNumIndex;
	}

	private static void swap(int[] arr, int i, int j) {
		if (i == j) {
			return;
		}
		int temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
	}

	private static void print(int[] arr) {
		for (int num : arr) {
			System.out.print(num + " ");
		}
	}

}
```