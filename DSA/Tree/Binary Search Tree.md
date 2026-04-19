```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node* left;
    struct node* right;
};

// Create node
struct node* createnode(int val) {
    struct node* temp = (struct node*)malloc(sizeof(struct node));
    temp->data = val;
    temp->left = NULL;
    temp->right = NULL;
    return temp;
}

// Insert
struct node* insert(struct node* root, int val) {
    if (root == NULL)
        return createnode(val);

    if (val < root->data)
        root->left = insert(root->left, val);
    else if (val > root->data)
        root->right = insert(root->right, val);

    return root;
}

// Find maximum (inorder predeccessor)
struct node* findMax(struct node* root) {
    while (root->right != NULL)
        root = root->right;
    return root;
}

// Delete node
struct node* deleteNode(struct node* root, int key) {
    if (root == NULL)
        return NULL;

    if (key < root->data) {
        root->left = deleteNode(root->left, key);
    }
    else if (key > root->data) {
        root->right = deleteNode(root->right, key);
    }
    else {
        // Case 1: No child
        if (root->left == NULL && root->right == NULL) {
            free(root);
            return NULL;
        }
        // Case 2: One child
        else if (root->left == NULL) {
            struct node* temp = root->right;
            free(root);
            return temp;
        }
        else if (root->right == NULL) {
            struct node* temp = root->left;
            free(root);
            return temp;
        }
        // Case 3: Two children
        else {
            struct node* temp = findMax(root->left);
            root->data = temp->data;
            root->left = deleteNode(root->left, temp->data);
        }
    }
    return root;
}

// Inorder traversal
void inorder(struct node* root) {
    if (root == NULL) return;
    inorder(root->left);
    printf("%d ", root->data);
    inorder(root->right);
}

// Main
int main() {
    struct node* root = NULL;

    int arr[] = {5, 3, 7, 2, 4, 6, 8};
    int n = 7;

    for (int i = 0; i < n; i++) {
        root = insert(root, arr[i]);
    }

    printf("Inorder before deletion: ");
    inorder(root);

    // Delete a node
    root = deleteNode(root, 7);

    printf("\nInorder after deletion: ");
    inorder(root);

    return 0;
}
```
