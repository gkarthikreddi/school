## Merge Sort
```java
class Mergesort
{
    void merge(int arr[], int l, int m, int r)
    {
        int n1 = m - l + 1;
        int n2 = r - m;
        int L[] = new int [n1];
        int R[] = new int [n2];
        for (int i=0; i<n1; ++i)
            L[i] = arr[l + i];
        for (int j=0; j<n2; ++j)
            R[j] = arr[m + 1+ j];
        int i = 0, j = 0;
        int k = l;
        while (i < n1 && j < n2)
        {
            if (L[i] <= R[j])
            {
                arr[k] = L[i];
                i++;
            }
            else
            {
                arr[k] = R[j];
                j++;
            }
            k++;
        }
        while (i < n1)
        {
            arr[k] = L[i];
            i++;
            k++;
        }
        while (j < n2)
        {
            arr[k] = R[j];
            j++;
            k++;
        }
    }
    
    void sort(int arr[], int l, int r)
    {
        if (l < r)
        {
            int m = (l+r)/2;
            sort(arr, l, m);
            sort(arr , m+1, r);
            merge(arr, l, m, r);
        }
    }
    
    static void printArray(int arr[])
    {
        int n = arr.length;
        for (int i=0; i<n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
    
    public static void main(String args[])
    {
        int arr[] = {12, 11, 13, 5, 6, 7};
        System.out.println("Given Array");
        printArray(arr);
        Mergesort ob = new Mergesort();
        ob.sort(arr, 0, arr.length-1);
        System.out.println("\nSorted array");
        printArray(arr);
    }
```
## Quick Sort
```java
import java.util.Arrays;

public class QuickSortDemo{
    public static void main(String args[]) {
        int[] unsorted = {6, 5, 3, 1, 8, 7, 2, 4};
        System.out.println("Unsorted array :" + Arrays.toString(unsorted));
        QuickSort algorithm = new QuickSort();
        algorithm.sort(unsorted);
        System.out.println("Sorted array :" + Arrays.toString(unsorted));
    }
}

class QuickSort {
    private int input[];
    private int length;

    public void sort(int[] numbers) {
        if (numbers == null || numbers.length == 0) {
            return;
        }
        this.input = numbers;
        length = numbers.length;
        quickSort(0, length - 1);
    }

    private void quickSort(int low, int high) {
        int i = low;
        int j = high;
        int pivot = input[low + (high - low) / 2];
        while (i <= j) {
            while (input[i] < pivot) {
                i++;
            }
            while (input[j] > pivot) {
                j--;
            }
            if (i <= j) {
                swap(i, j);
                i++;
                j--;
            }
        }
        if (low < j) {
            quickSort(low, j);
        }
        if (i < high) {
            quickSort(i, high);
        }
    }

    private void swap(int i, int j) {
        int temp = input[i];
        input[i] = input[j];
        input[j] = temp;
    }
}
```
## Depth First Search
```java
import java.util.InputMismatchException;
import java.util.Scanner;
import java.util.Stack;

public class DFS
{
    private Stack<Integer> stack;
    public DFS()
    {
        stack = new Stack<Integer>();
    }

    public void dfs(int adjacency_matrix[][], int source)
    {
        int number_of_nodes = adjacency_matrix[source].length - 1;
        int visited[] = new int[number_of_nodes + 1];
        int element = source;
        int i = source;
        System.out.print(element + "\t");
        visited[source] = 1;
        stack.push(source);
        while (!stack.isEmpty())
        {
            element = stack.peek();
            i = element;
            while (i <= number_of_nodes)
            {
                if (adjacency_matrix[element][i] == 1 && visited[i] == 0)
                {
                    stack.push(i);
                    visited[i] = 1;
                    element = i;
                    i = 1;
                    System.out.print(element + "\t");
                    continue;
                }
                i++;
            }
            stack.pop();
        }
    }
    public static void main(String...arg)
    {
        int number_of_nodes, source;
        Scanner scanner = null;
        try
        {
            System.out.println("Enter the number of nodes in the graph");
            scanner = new Scanner(System.in);
            number_of_nodes = scanner.nextInt();
            int adjacency_matrix[][] = new int[number_of_nodes + 1][number_of_nodes + 1];
            System.out.println("Enter the adjacency matrix");
            for (int i = 1; i <= number_of_nodes; i++)
                for (int j = 1; j <= number_of_nodes; j++)
                    adjacency_matrix[i][j] = scanner.nextInt();
            System.out.println("Enter the source for the graph");
            source = scanner.nextInt();
            System.out.println("The DFS Traversal for the graph is given by ");
            DFS dfs = new DFS();
            dfs.dfs(adjacency_matrix, source);
        }catch(InputMismatchException inputMismatch)
        {
            System.out.println("Wrong Input format");
        }
        scanner.close();
    }
}
```
### Output
>Enter the number of nodes in the graph\
>4\
>Enter the adjacency matrix\
>0 1 0 1\
>0 0 1 0\
>0 1 0 1\
>0 0 0 1\
>Enter the source for the graph\
>1\
>The DFS Traversal for the graph is given by\
>1	2	3	4
## Breadth First Search
```java
import java.util.InputMismatchException;
import java.util.Scanner;
import java.util.Stack;

public class DFS
{
    private Stack<Integer> stack;
    public DFS()
    {
        stack = new Stack<Integer>();
    }

    public void dfs(int adjacency_matrix[][], int source)
    {
        int number_of_nodes = adjacency_matrix[source].length - 1;
        int visited[] = new int[number_of_nodes + 1];
        int element = source;
        int i = source;
        System.out.print(element + "\t");
        visited[source] = 1;
        stack.push(source);
        while (!stack.isEmpty())
        {
            element = stack.peek();
            i = element;
            while (i <= number_of_nodes)
            {
                if (adjacency_matrix[element][i] == 1 && visited[i] == 0)
                {
                    stack.push(i);
                    visited[i] = 1;
                    element = i;
                    i = 1;
                    System.out.print(element + "\t");
                    continue;
                }
                i++;
            }
            stack.pop();
        }
    }
    public static void main(String...arg)
    {
        int number_of_nodes, source;
        Scanner scanner = null;
        try
        {
            System.out.println("Enter the number of nodes in the graph");
            scanner = new Scanner(System.in);
            number_of_nodes = scanner.nextInt();
            int adjacency_matrix[][] = new int[number_of_nodes + 1][number_of_nodes + 1];
            System.out.println("Enter the adjacency matrix");
            for (int i = 1; i <= number_of_nodes; i++)
                for (int j = 1; j <= number_of_nodes; j++)
                    adjacency_matrix[i][j] = scanner.nextInt();
            System.out.println("Enter the source for the graph");
            source = scanner.nextInt();
            System.out.println("The DFS Traversal for the graph is given by ");
            DFS dfs = new DFS();
            dfs.dfs(adjacency_matrix, source);
        }catch(InputMismatchException inputMismatch)
        {
            System.out.println("Wrong Input format");
        }
        scanner.close();
    }
}
```
### Output
>Enter the number of nodes in the graph\
>4\
>Enter the adjacency matrix\
>0 1 0 1\
>0 0 1 0\
>0 1 0 1\
>0 0 0 1\
>Enter the source for the graph\
>1\
>The DFS Traversal for the graph is given by\
>1	2	3	4
## Job Sequencing
```java
import java.util.*;

public class Job
{
    public static void main(String args[])
    {
        Scanner sc=new Scanner(System.in);
        System.out.println("Enter the number of Jobs");
        int n=sc.nextInt();
        String a[]=new String[n];
        int b[]=new int[n];
        int c[]=new int[n];
        for(int i=0;i<n;i++)
        {
            System.out.println("Enter the Jobs");
            a[i]=sc.next();
            System.out.println("Enter the Profit");
            b[i]=sc.nextInt();
            System.out.println("Enter the DeadLine");
            c[i]=sc.nextInt();
        }
        System.out.println("--Arranged Order--\nJobs: ");
        for(int i=0;i<n;i++)
        {
            System.out.print(a[i]+" ");
        }
        System.out.print("\nProfit: ");
        for(int i=0;i<n;i++)
        {
            System.out.print(b[i]+" ");
        }
        System.out.print("\nDeadLine:");
        for(int i=0;i<n;i++)
        {
            System.out.print(c[i]+" ");
        }
        for(int i=0;i<n-1;i++)
        {
            for(int j=i+1;j<n;j++)
            {
                if(b[i]<b[j])
                {
                    int temp=b[i];
                    b[i]=b[j];
                    b[j]=temp;
                    temp=c[i];
                    c[i]=c[j];
                    c[j]=temp;
                    String temp1=a[i];
                    a[i]=a[j];
                    a[j]=temp1;
                }
            }
        }
        System.out.println("\n--Sorted Order--\nJobs: ");
        for(int i=0;i<n;i++)
        {
            System.out.print(a[i]+" ");
        }
        System.out.print("\nProfit: ");
        for(int i=0;i<n;i++)
        {
            System.out.print(b[i]+" ");
        }
        System.out.print("\nDeadLine:");
        for(int i=0;i<n;i++)
        {
            System.out.print(c[i]+" ");
        }
        System.out.println();
        int max=c[0];
        for(int i=0;i<n;i++)
        {
            if(c[i]>max)
            {
                max=c[i];
            }
        }
        String x[]=new String[max];
        int xx[]=new int[max];
        int profit=0;
        for(int i=0;i<n;i++)
        {
            int pp=c[i];
            pp=pp-1;
            if(x[pp]==null )
            {
                x[pp]=a[i];
                profit+=b[i];
            }
            else
            {
                while(pp!=-1)
                {
                    if(x[pp]==null)
                    {
                        x[pp]=a[i];
                        profit+=b[i];
                        break;
                    }
                    pp=pp-1;
                }
            }
        }
        for(int i=0;i<max;i++)
        {
            System.out.print("-->"+x[i]);
        }
        System.out.print("\nProfit Earned"+profit);
    }
}
```
## NQueen Problem 
```java
public class NQueenProblem {
    final int N = 8;
    void printSolution(int board[][])
    {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++)
                System.out.print(" " + board[i][j]+ " ");
            System.out.println();
        }
    }
    boolean isSafe(int board[][], int row, int col)
    {
        int i, j;
        for (i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;
        for (i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;
        for (i = row, j = col; j >= 0 && i < N; i++, j--)
            if (board[i][j] == 1)
                return false;
        return true;
    }
    boolean solveNQUtil(int board[][], int col)
    {
        if (col >= N)
            return true;
        for (int i = 0; i < N; i++) {
            if (isSafe(board, i, col)) {
                board[i][col] = 1;
                if (solveNQUtil(board, col + 1) == true)
                    return true;
                board[i][col] = 0; // BACKTRACK
            }
        }
        return false;
    }
    boolean solveNQ()
    {
        int board[][] = { { 0, 0, 0, 0 ,0,0,0,0},
            { 0, 0, 0, 0 ,0,0,0,0},
            { 0, 0, 0, 0,0,0,0,0},
            { 0, 0, 0, 0 ,0,0,0,0},
            {0,0,0,0,0,0,0,0},
            {0,0,0,0,0,0,0,0},
            {0,0,0,0,0,0,0,0},
            {0,0,0,0,0,0,0,0}};
        if (solveNQUtil(board, 0) == false) {
            System.out.print("Solution does not exist");
            return false;
        }
        printSolution(board);
        return true;
    }
    public static void main(String args[])
    {
        NQueenProblem Queen = new NQueenProblem();
        Queen.solveNQ();
    }
}
```
## Sum of Subsets
```java
import java.util.Scanner;

public class SumOfSubsets {
    int[] w;
    int[] x;
    int sum;
    public void process() {
        getData();
    }
    private void getData() {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter the number of elements:");
        int n = sc.nextInt();
        w = new int[n + 1];
        x = new int[n + 1];
        int total = 0;
        System.out.println("Enter " + n + " Elements :");
        for (int i = 1; i < n + 1; i++) {
            w[i] = sc.nextInt();
            total += w[i];
        }
        System.out.println("Enter the sum to be obtained: ");
        sum = sc.nextInt();
        if (total < sum) {
            System.out.println("Not possible to obtain the subset!!!");
            System.exit(1);
        }
        subset(0, 1, total);
    }
    private void subset(int s, int k, int r) {
        int i = 0;
        x[k] = 1;
        if (s + w[k] == sum) {
            System.out.println();
            for (i = 1; i <= k; i++) {
                System.out.print("\t" + x[i]);
            }
        } else if ((s + w[k] + w[k + 1]) <= sum) {
            subset(s + w[k], k + 1, r - w[k]);
        }
        if ((s + r - w[k]) >= sum && (s + w[k + 1]) <= sum) {
            x[k] = 0;
            subset(s, k + 1, r - w[k]);
        }
    }
    public static void main(String[] args) {
        new SumOfSubsets().process();
    }
}
```
### Output
>Enter the number of elements:4\
Enter 4 Elements :\
7\
11\
13\
24\
Enter the sum to be obtained:\
31\
1	1	1\
1	0	0	1
## Graph Coloring
```java
import java.util.Scanner;

public class GraphColoring
{
    private int V, numOfColors;
    private int[] color;
    private int[][] graph;
    public void graphColor(int[][] g, int noc)
    {
        V = g.length;
        numOfColors = noc;
        color = new int[V];
        graph = g;
        try
        {
            solve(0);
            System.out.println("No solution");
        }
        catch (Exception e)
        {
            System.out.println("\nSolution exists ");
            display();
        }
    }
    public void solve(int v) throws Exception
    {
        if (v == V)
            throw new Exception("Solution found");
        for (int c = 1; c <= numOfColors; c++)
        {
            if (isPossible(v, c))
            {
                color[v] = c;
                solve(v + 1);
                color[v] = 0;
            }
        }
    }
    public boolean isPossible(int v, int c)
    {
        for (int i = 0; i < V; i++)
            if (graph[v][i] == 1 && c == color[i])
                return false;
        return true;
    }
    public void display()
    {
        System.out.print("\nColors : ");
        for (int i = 0; i < V; i++)
            System.out.print(color[i] +" ");
        System.out.println();
    }
    public static void main (String[] args)
    {
        Scanner scan = new Scanner(System.in);
        System.out.println("Graph Coloring Algorithm Test\n");
        GraphColoring gc = new GraphColoring();
        System.out.println("Enter number of verticesz\n");
        int V = scan.nextInt();
        System.out.println("\nEnter matrix\n");
        int[][] graph = new int[V][V];
        for (int i = 0; i < V; i++)
            for (int j = 0; j < V; j++)
                graph[i][j] = scan.nextInt();
        System.out.println("\nEnter number of colors");
        int c = scan.nextInt();
        gc.graphColor(graph, c);
    }
}
```
### Output
>Graph Coloring Algorithm Test\
Enter number of vertices\
4\
Enter matrix\
1 0 1 0\
0 0 0 1\
1 1 1 0\
1 0 0 1\
Enter number of colors\
2\
Solution exists\
Colors : 1 1 2 2
