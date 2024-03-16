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
## Shortest Parth 
```java
import java.util.*;

public class Dijkstra
{
    public int distance[] = new int[10];
    public int cost[][] = new int[10][10];
    public void calc(int n,int s)
    {
        int flag[] = new int[n+1];
        int i,minpos=1,k,c,minimum;
        for(i=1;i<=n;i++)
        {
            flag[i]=0;
            this.distance[i]=this.cost[s][i];
        }
        c=2;
        while(c<=n)
        {
            minimum=99;
            for(k=1;k<=n;k++)
            {
                if(this.distance[k]<minimum && flag[k]!=1)
                {
                    minimum=this.distance[i];
                    minpos=k;
                }
            }
            flag[minpos]=1;
            c++;
            for(k=1;k<=n;k++)
            {
                if(this.distance[minpos]+this.cost[minpos][k] < this.distance[k] && flag[k]!=1 )
                    this.distance[k]=this.distance[minpos]+this.cost[minpos][k];
            }
        }
    }
    public static void main(String args[])
    {
        int nodes,source,i,j;
        Scanner in = new Scanner(System.in);
        System.out.println("Enter the Number of Nodes \n");
        nodes = in.nextInt();
        Dijkstra d = new Dijkstra();
        System.out.println("Enter the Cost Matrix Weights: \n");
        for(i=1;i<=nodes;i++)
            for(j=1;j<=nodes;j++)
            {
                d.cost[i][j]=in.nextInt();
                if(d.cost[i][j]==0)
                    d.cost[i][j]=999;
            }
        System.out.println("Enter the Source Vertex :\n");
        source=in.nextInt();
        d.calc(nodes,source);
        System.out.println("The Shortest Path from Source \t"+source+"\t to all other vertices are : \n");
        for(i=1;i<=nodes;i++)
            if(i!=source)
                System.out.println("source :"+source+"\t destination :"+i+"\t MinCost is :"+d.distance[i]+"\t");
    }
}
```
### Output
>Enter the Number of Nodes\
>4\
>Enter the Cost Matrix Weights:\
>0 3 0 7\
>3 0 4 2\
>0 4 0 5\
>7 2 5 0\
>Enter the Source Vertex :\
>1\
>The Shortest Path from Source 	1	 to all other vertices are :\
>source :1	 destination :2	 MinCost is :3\
>source :1	 destination :3	 MinCost is :7\
>source :1	 destination :4	 MinCost is :5
## Spanning Tree
```java
import java.util.InputMismatchException;
import java.util.Scanner;

public class Prims
{
    private boolean unsettled[];
    private boolean settled[];
    private int numberofvertices;
    private int adjacencyMatrix[][];
    private int key[];
    public static final int INFINITE = 999;
    private int parent[];
    public Prims(int numberofvertices)
    {
        this.numberofvertices = numberofvertices;
        unsettled = new boolean[numberofvertices + 1];
        settled = new boolean[numberofvertices + 1];
        adjacencyMatrix = new int[numberofvertices + 1][numberofvertices + 1];
        key = new int[numberofvertices + 1];
        parent = new int[numberofvertices + 1];
    }
    public int getUnsettledCount(boolean unsettled[])
    {
        int count = 0;
        for (int index = 0; index < unsettled.length; index++)
        {
            if (unsettled[index])
            {
                count++;
            }
        }
        return count;
    }
    public void primsAlgorithm(int adjacencyMatrix[][])
    {
        int evaluationVertex;
        for (int source = 1; source <= numberofvertices; source++)
        {
            for (int destination = 1; destination <= numberofvertices; destination++)
            {
                this.adjacencyMatrix[source][destination] =
                    adjacencyMatrix[source][destination];
            }
        }
        for (int index = 1; index <= numberofvertices; index++)
        {
            key[index] = INFINITE;
        }
        key[1] = 0;
        unsettled[1] = true;
        parent[1] = 1;
        while (getUnsettledCount(unsettled) != 0)
        {
            evaluationVertex = getMimumKeyVertexFromUnsettled(unsettled);
            unsettled[evaluationVertex] = false;
            settled[evaluationVertex] = true;
            evaluateNeighbours(evaluationVertex);
        }
    }
    private int getMimumKeyVertexFromUnsettled(boolean[] unsettled2)
    {
        int min = Integer.MAX_VALUE;
        int node = 0;
        for (int vertex = 1; vertex <= numberofvertices; vertex++)
        {
            if (unsettled[vertex] == true && key[vertex] < min)
            {
                node = vertex;
                min = key[vertex];
            }
        }
        return node;
    }
    public void evaluateNeighbours(int evaluationVertex)
    {
        for (int destinationvertex = 1; destinationvertex <= numberofvertices;
                destinationvertex++)
        {
            if (settled[destinationvertex] == false)
            {
                if (adjacencyMatrix[evaluationVertex][destinationvertex] != INFINITE)
                {
                    if (adjacencyMatrix[evaluationVertex][destinationvertex] <
                            key[destinationvertex])
                    {
                        key[destinationvertex] =
                            adjacencyMatrix[evaluationVertex][destinationvertex];
                        parent[destinationvertex] = evaluationVertex;
                    }
                    unsettled[destinationvertex] = true;
                }
            }
        }
    }
    public void printMST()
    {
        System.out.println("SOURCE : DESTINATION = WEIGHT");
        for (int vertex = 2; vertex <= numberofvertices; vertex++)
        {
            System.out.println(parent[vertex] + "\t:\t" + vertex +"\t=\t"+
                    adjacencyMatrix[parent[vertex]][vertex]);
        }
    }
    public static void main(String... arg)
    {
        int adjacency_matrix[][];
        int number_of_vertices;
        Scanner scan = new Scanner(System.in);
        try
        {
            System.out.println("Enter the number of vertices");
            number_of_vertices = scan.nextInt();
            adjacency_matrix = new int[number_of_vertices + 1][number_of_vertices + 1];
            System.out.println("Enter the Weighted Matrix for the graph");
            for (int i = 1; i <= number_of_vertices; i++)
            {
                for (int j = 1; j <= number_of_vertices; j++)
                {
                    adjacency_matrix[i][j] = scan.nextInt();
                    if (i == j)
                    {
                        adjacency_matrix[i][j] = 0;
                        continue;
                    }
                    if (adjacency_matrix[i][j] == 0)
                    {
                        adjacency_matrix[i][j] = INFINITE;
                    }
                }
            }
            Prims prims = new Prims(number_of_vertices);
            prims.primsAlgorithm(adjacency_matrix);
            prims.printMST();
        } catch (InputMismatchException inputMismatch)
        {
            System.out.println("Wrong Input Format");
        }
        scan.close();
    }
}
```
### Output
>Enter the number of vertices\
>5\
>Enter the Weighted Matrix for the graph\
>0 4 0 0 5\
>4 0 3 6 1\
>0 3 0 6 2\
>0 6 6 0 7\
>5 1 2 7 0\
>SOURCE : DESTINATION = WEIGHT\
>1	:	2	=	4\
>5	:	3	=	2\
>2	:	4	=	6\
>2	:	5	=	1