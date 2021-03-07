## GraphNode

```java
public class GraphNode {
    public int value;
    //public List<GraphNode> nei;
    public Map<GraphNode, Integer> nei;
    boolean visited;
    public GraphNode(int value) {
        this.value = value;
        //nei = new ArrayList<>();
        nei = new HashMap<>();
        visited = false;
    }
}
```

---

## Convert a 2D array to Adjacency List and Adjacency Matrix

```markdown
[node1, node2, weight]
The weight between node1 and node2.
edges = [[0,1,100],[1,2,100],[0,2,500]]
                
                  0
            100/     \ 500
              /       \
             1 ------ 2
                100           
                
```

## Adjacency Map

```java
public class AdjacencyMap {

    public static Map<Integer, Map<Integer, Integer>> DirectedGraph(int[][] input) {
        Map<Integer, Map<Integer, Integer>> map = new HashMap<>();
        for (int[] arr : input) {
            if (!map.containsKey(arr[0])) {
                map.put(arr[0], new HashMap<>());
            }
            map.get(arr[0]).put(arr[1], arr[2]);
        }
        return map;
    }

    public static Map<Integer, Map<Integer, Integer>> UndirectedGraph(int[][] input) {
        Map<Integer, Map<Integer, Integer>> map = new HashMap<>();
        for (int[] arr : input) {
            if (!map.containsKey(arr[0])) {
                map.put(arr[0], new HashMap<>());
            }
            map.get(arr[0]).put(arr[1], arr[2]);

            if (!map.containsKey(arr[1])) {
                map.put(arr[1], new HashMap<>());
            }
            map.get(arr[1]).put(arr[0], arr[2]);
        }
        return map;
    }
}
/*
output:
{0={1=100, 2=500}, 1={0=100, 2=100}, 2={0=500, 1=100}}
```

## Adjacency List

```java
public class AdjacencyList {

    public static List<List<int[]>> DirectedGraph(int[][] input) {
        List<List<int[]>> graph = new ArrayList<>();
        for (int i = 0; i < input.length; i++) {
            graph.add(new ArrayList<>());
        }
        for (int[] arr : input) {
            graph.get(arr[0]).add(new int[] {arr[1], arr[2]});
        }
        return graph;
    }

    public static List<List<int[]>> UndirectedGraph(int[][] input) {
        List<List<int[]>> graph = new ArrayList<>();
        for (int i = 0; i < input.length; i++) {
            graph.add(new ArrayList<>());
        }
        for (int[] arr : input) {
            graph.get(arr[0]).add(new int[] {arr[1], arr[2]});
            graph.get(arr[1]).add(new int[] {arr[0], arr[2]});
        }
        return graph;
    }
}
/*
output:
[[[1, 100][2, 500]]
 [[0, 100][2, 100]]
 [[1, 100][0, 500]]]
```

## Adjacency Matrix

```java
public class AdjacencyMatrix {
    public int[][] DirectedGraph(int[][] input) {
        int[][] matrix = new int[input.length][input.length];
        for (int[] arr : input) {
            matrix[arr[0]][arr[1]] = arr[2];
        }
        return matrix;
    }

    public int[][] UndirectedGraph(int[][] input) {
        int[][] matrix = new int[input.length][input.length];
        for (int[] arr : input) {
            matrix[arr[0]][arr[1]] = arr[2];
            matrix[arr[1]][arr[0]] = arr[2];
        }
        return matrix;
    }
}
/*
output:
[[0, 100, 500], [100, 0, 100], [500, 100, 0]]
```

