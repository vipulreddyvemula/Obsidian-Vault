Creating graph using adjacent list 
```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX_VERTICES 100

// Adjacency list node
struct Node {
    int data;
    struct Node* next;
};

// Graph structure
struct Graph {
    int vertices;
    struct Node* adj[MAX_VERTICES];
};

// Create new node
struct Node* createNode(int v) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = v;
    newNode->next = NULL;
    return newNode;
}

// Create graph
struct Graph* createGraph(int vertices) {
    struct Graph* graph = (struct Graph*)malloc(sizeof(struct Graph));
    graph->vertices = vertices;

    for (int i = 0; i < vertices; i++)
        graph->adj[i] = NULL;

    return graph;
}

// Add edge (undirected)
void addEdge(struct Graph* graph, int u, int v) {
    // u → v
    struct Node* newNode = createNode(v);
    newNode->next = graph->adj[u];
    graph->adj[u] = newNode;

    // v → u
    newNode = createNode(u);
    newNode->next = graph->adj[v];
    graph->adj[v] = newNode;
}

// DFS (recursive)
void DFS(struct Graph* graph, int vertex, bool visited[]) {
    visited[vertex] = true;
    printf("%d ", vertex);

    struct Node* temp = graph->adj[vertex;

    while (temp != NULL) {
        int adjVertex = temp->data;

        if (!visited[adjVertex]) {
            DFS(graph, adjVertex, visited);
        }
        temp = temp->next;
    }
}

// Wrapper
void DFS_start(struct Graph* graph, int start) {
    bool visited[MAX_VERTICES] = {false};
    printf("DFS traversal: ");
    DFS(graph, start, visited);
    printf("\n");
}

// Main
int main() {
    int vertices = 6;
    struct Graph* graph = createGraph(vertices);

    // same graph as before
    addEdge(graph, 0, 1);
    addEdge(graph, 0, 2);
    addEdge(graph, 1, 3);
    addEdge(graph, 1, 4);
    addEdge(graph, 2, 5);
    addEdge(graph, 3, 5);
    addEdge(graph, 4, 5);

    DFS_start(graph, 0);

    return 0;
}
```
