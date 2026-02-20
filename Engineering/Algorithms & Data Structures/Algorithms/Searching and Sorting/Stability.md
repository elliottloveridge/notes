# Stability
- Stability for algorithms is their ability to retain original order for multiple inputs
- Given an array of tuples (student, score) sorted alphabetically like below;
	- `l = [('Ariel', 50), ('Aj', 80), ('Bart', 50), ('Cj', 80)]`
- If you are sorting by score using a stable algorithm it will ensure that, if you have two students with the same score, they will stay in the same order as the original list
	- An unstable algorithm however can produce any output as long as the scores are in the right order when sorted

- Stable sort algorithms:
	- Bubble sort, insertion sort, merge sort
		- Bubble sort compares adjacent algorithms
			- If two same items appear one after another it will not swap them (hence stable)
- Unstable sort algorithms
	- Selection sort, quick sort, heap sort
		- Selection sort finds the maximum element and swaps it with last element
			-  This can break the order
