# Competetive Programming Questions for Interviews Practise . Questions and My Solutions 
## Kindly Contribute 
## Add your name Here and see new Questions in issues 


You may answer in any language you feel comfortable but only 1 submission per request will be accepted .

/*
 * C Program to Check whether a Tree is a Binary Search Tree 
 */

#include <stdio.h>
#include <stdlib.h>
 
struct node
{
    int data;
    struct node* left;
    struct node* right;
};
 
static struct node *prev = NULL; 
 
/*Function to check whether the tree is BST or not*/
/*
 * C Program to Check whether a Tree is a Binary Search Tree
 */

#include <stdio.h>
#include <stdlib.h>

struct node
{
    int data;
    struct node* left;
    struct node* right;
};

static struct node *prev = NULL;

/*Function to check whether the tree is BST or not*/
int is_bst(struct node* root)
{
    if (root)
    {
        if (!is_bst(root->left)) //moves towards the leftmost child of the tree and checks for the BST
            return 0;
        if (prev != NULL && root->data <= prev->data)
            return 0;
        prev = root;
        return is_bst(root->right);    //moves the corresponding right child of the tree and checks for the BST
    }
    return 1;
}

struct node* newNode(int data)
{
    struct node* node = (struct node*)malloc(sizeof(struct node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;

    return(node);
}

int main()
{
    struct node *root = newNode(40);
    root->left        = newNode(20);
    root->right       = newNode(5);
    root->left->left  = newNode(30);
    root->left->right = newNode(20);
    root->right->right = newNode(80);
    root->right->right->right = newNode(90);
    if (is_bst(root))
        printf("TREE Is BST");
    else
        printf("TREE Not a BST");
    prev = NULL;
    return 0;
}
