# Lexicographically-Smallest-Subsequence

In a distant land, Todo has an array of numbers, Arr, and a magic number K. He wants to find the smallest possible sequence of exactly K numbers from Arr (keeping their original order). Help Todo find this lexicographically smallest subsequence!

Input
The first line of input contains two space-separated integers N and K.
The second line of the input contains N integers denoting array Arr.

Constraints
1 ≤ K ≤ N ≤ 105
1 ≤ Arr[i] ≤ 109
Output
Print K space separated integers denoting the lexicographically smallest subsequence of the array of size K.

# Input reading
N, K = map(int, input().split())
Arr = list(map(int, input().split()))

# Stack to build the result
stack = []
remaining = K  # Remaining elements needed

for i in range(N):
    # Remove elements from the stack if they are larger and we can still form a valid subsequence
    while stack and stack[-1] > Arr[i] and len(stack) + (N - i) > K:
        stack.pop()
    # Add the current element to the stack if there's room
    if len(stack) < K:
        stack.append(Arr[i])

# Output the result
print(' '.join(map(str, stack)))
