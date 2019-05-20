## Here are some images of projects I developed 
[Elijah Lamoureux's Profile](https://elijahlamoureux.portfoliobox.net/)

### Here is a simple Binary Tree used to sort names alphabetically. 

```c++
#include <iostream>
#include <string>
#include "BinaryTreeApplication.h"
using namespace std; 

class Bnode {
public:
	string val;																/* Each of the pointers, pLeft and pRight, can either have a null value or point to a child node. Either or both of the pointers may be null -- */
	Bnode* pLeft;															/* a null value indicating there is currently no child on that side. If both pointers are null, the node object is a "leaf" or terminus that currently has no children.*/
	Bnode* pRight;
	Bnode(string s) { val = s; pLeft = pRight = nullptr; }
};

class Btree {
public:
	Btree() { root = nullptr; }
	void insert(string s)
	{
		root = insert_at_sub(s, root);
		nSize++;
	}
	void print() { print_sub(root); cout << get_size() << endl; }
	int get_size() { return nSize; }
	int get_size_of_subtree() { return size_of_subtree(root); }
	bool find_node(string s) { return search_node(root, s); }


private:
	Bnode* root;
	Bnode* insert_at_sub(string s, Bnode* p);
	void print_sub(Bnode* p);
	int nSize = 0;
	int nSubtreeSize = 0;
	int size_of_subtree(Bnode* p);
	bool search_node(Bnode* p, string s);

};

Bnode* Btree::insert_at_sub(string s, Bnode* p) {
	if (!p) {
		return new Bnode(s);
	}
	else if (s < p->val) {
		p->pLeft = insert_at_sub(s, p->pLeft);
	}
	else if (s > p->val) {
		p->pRight = insert_at_sub(s, p->pRight);
	}
	return p;
}

void Btree::print_sub(Bnode* p) {
	if (p) {
		print_sub(p->pLeft);
		cout << p->val << endl;
		print_sub(p->pRight);
	}
}

int Btree::size_of_subtree(Bnode* p) {

	if (p) {									/* Check to see if there is a value, if so, we keep checking if anything is to the left of the node */
		size_of_subtree(p->pLeft);				/* Once we checked all the nodes on the left, it will return to the previous node's function */
		nSubtreeSize++;							/* If there is nothing on the left, we mark the value and check if there is a value on the right */
		size_of_subtree(p->pRight);				/* If there is a value on the right, we will check if there is a value on the left. If not, we simply return to the previous node*/
	}
	return nSubtreeSize;
}

//This is a test. 
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes
This theme is powered by [Jekyll](https://jekyllrb.com/)

### Contact Me
You can reach out to me through my email at elijahlamoureux@gmail.com. 
