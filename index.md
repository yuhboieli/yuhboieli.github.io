# Here are some images of projects I developed 
[Elijah Lamoureux's Profile](https://elijahlamoureux.portfoliobox.net/)

### Here is a simple Binary Tree used to sort names alphabetically. 

<details><summary>View My Code</summary>
<p>
	
```c++
#include <iostream>
#include <string>
#include "BinaryTreeApplication.h"
using namespace std; 

class Bnode {
public:
	string val;															
	Bnode* pLeft;		
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
	if (p) {									
		size_of_subtree(p->pLeft);				
		nSubtreeSize++;							
		size_of_subtree(p->pRight);				
	}
	return nSubtreeSize;
}

int main() {
	Btree my_tree;
	string sPrompt = "Enter a name (ENTER when done): ";
	string sInput = "";

	while (true) {
		cout << sPrompt;
		getline(cin, sInput);
		if (sInput.size() == 0) {
			break;
		}

		my_tree.insert(sInput);
	}

	cout << "Here are the names, in order." << endl;
	my_tree.print();
	cout << my_tree.get_size_of_subtree() << endl;

}

// Elijah Lamoureux, More iterations to come.... 
```


</p>
</details>



For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes
This theme is powered by [Jekyll](https://jekyllrb.com/)

### Contact Me
You can reach out to me through my email at **elijahlamoureux@gmail.com**. 
