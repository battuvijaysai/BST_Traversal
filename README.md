#include <stdio.h>
#include <stdlib.h>
struct node {
    int data;
    struct node* left;
    struct node* right;
};
struct node *newnode(int data)
{
    struct node* node = (struct node*)malloc(sizeof(struct node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;

    return (node);
}
int printPostorder(struct node* node)
{
    if (node == NULL)
        return 0;
    printPostorder(node->left);
    printPostorder(node->right);
    printf("%d ", node->data);
}
int printInorder(struct node* node)
{
    if (node == NULL)
        return 0;
    printInorder(node->left);
    printf("%d ", node->data);
    printInorder(node->right);
}
int printPreorder(struct node* node)
{
    if (node == NULL)
        return 0;
    printf("%d ", node->data);
    printPreorder(node->left);
    printPreorder(node->right);
}
int main()
{
    struct node* root = newnode(1);
    root->left = newnode(2);
    root->right = newnode(3);
    root->left->left = newnode(4);
    root->left->right = newnode(5);

    printf("\nPreorder traversal of binary tree is \n");
    printPreorder(root);

    printf("\nInorder traversal of binary tree is \n");
    printInorder(root);

    printf("\nPostorder traversal of binary tree is \n");
    printPostorder(root);

    getchar();
    return 0;
}
