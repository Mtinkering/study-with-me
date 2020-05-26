## Permutations: N!
Permutations is when we want the same length, but different order.
E.g. from  'AABC', generate all permutations

Can use backtracking to solve this.

- https://leetcode.com/problems/letter-case-permutation/

## Combinations

C N k = (N−k)/(!k!N!)

Given a set of N characters, generate string of length k.

Can use backtracking to solve this
​	
- https://leetcode.com/problems/letter-tile-possibilities/
- https://leetcode.com/problems/the-k-th-lexicographical-string-of-all-happy-strings-of-length-n/
- https://leetcode.com/problems/iterator-for-combination/

# Subset
2^N, since each element could be absent or present.


//                       {  }
//               /                     \
//             { }                     {1}  - - - - - - - - - - - - - - > [(1),2,3] : i = 0
//          /       \             /          \
//       { }        {2}         {1}         {1,2} - - - - - - - - - - - > [1,(2),3] : i = 1
//      /   \      /   \       /   \        /   \
//    { }   {3}  {2}  {2,3}  {1}  {1,3}  {1,2}  {1,2,3} - - - - - - - - > [1,2,(3)] : i = 2


``` 
 Number of subsets for {1 , 2 , 3 } = 2^3 .
 why ? 
case    possible outcomes for the set of subsets
  1   ->          Take or dont take = 2 
  2   ->          Take or dont take = 2  
  3   ->          Take or dont take = 2 

therefore , total = 2*2*2 = 2^3 = { { } , {1} , {2} , {3} , {1,2} , {1,3} , {2,3} , {1,2,3} }

Lets assign bits to each outcome  -> First bit to 1 , Second bit to 2 and third bit to 3
Take = 1
Dont take = 0
 
0) 0 0 0  -> Dont take 3 , Dont take 2 , Dont take 1 = { } 
1) 0 0 1  -> Dont take 3 , Dont take 2 ,   take 1       =  {1 } 
2) 0 1 0  -> Dont take 3 ,    take 2       , Dont take 1 = { 2 } 
3) 0 1 1  -> Dont take 3 ,    take 2       ,      take 1    = { 1 , 2 } 
4) 1 0 0  ->    take 3      , Dont take 2  , Dont take 1 = { 3 } 
5) 1 0 1  ->    take 3      , Dont take 2  ,     take 1     = { 1 , 3 } 
6) 1 1 0  ->    take 3      ,    take 2       , Dont take 1 = { 2 , 3 } 
7) 1 1 1  ->    take 3     ,      take 2     ,      take 1     = { 1 , 2 , 3 } 

In the above logic ,Insert S[i] only if (j>>i)&1 ==true   { j E { 0,1,2,3,4,5,6,7 }   i = ith element in the input array }

element 1 is inserted only into athose places where 1st bit of j is 1 
   if( j >> 0 &1 )  ==> for above above eg. this is true for sl.no.( j )= 1 , 3 , 5 , 7 

element 2 is inserted only into those places where 2nd bit of j is 1 
   if( j >> 1 &1 )  == for above above eg. this is true for sl.no.( j ) = 2 , 3 , 6 , 7

element 3 is inserted only into those places where 3rd bit of j is 1 
   if( j >> 2 & 1 )  == for above above eg. this is true for sl.no.( j ) = 4 , 5 , 6 , 7 

Time complexity : O(n*2^n) , for every input element loop traverses the whole solution set length i.e. 2^n
 ```

 ```java
    // Bitmask
    class subset {
     public List<List<Integer>> subsets(int[] nums) {
        int n = nums.length;
         
        int subsetSize = 1 << n;
        List<List<Integer> ans = new ArrayList<>();
        List<Integer> el = new ArrayList<>(); 
        
        for (int i = 0; i < subsetSize; i++) {
            for (int j = 0; i < n; j++) {
                if (j >> i & 1 == 1) {
                    
                }
            }
        }
         
        return ans;
    }
    }
/*
000 0
001 1
010 2
011 3
100 4
101 5
110 6    
111 7    
1 << j
*/
```

# General strategy:

###1. Recursion

###2. Backtracking

Backtracking is an algorithm for finding all solutions by exploring all potential candidates. 
If the solution candidate turns to be not a solution (or at least not the last one), 
backtracking algorithm discards it by making some changes on the previous step, 
i.e. backtracks and then try again.

###3. Lexicographic generation based on the mapping between binary bitmasks and the corresponding
permutations / combinations / subsets.