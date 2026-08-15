# 1670. Design Front Middle Back Queue

**Difficulty:** Medium  
**Topics:** Double Pointer Linked List  
**LeetCode:** https://leetcode.com/problems/design-front-middle-back-queue/description/   

---

## Solution 1 - Double Pointer Linked Lis

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(1)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class FrontMiddleBackQueue {
public:
    struct Node
    {
        Node *prev;
        Node *next;
        int data;
        Node(int val)
        {
            data = val;
            prev = next = NULL;
        }
    };
    Node *front, *last, *mid;
    int total;
    FrontMiddleBackQueue() {
        front = last = mid = NULL;
        total = 0;
    }
    
    void pushFront(int val) {
        Node *node = new Node(val);
        total++;
        if(front==NULL)
        {   
            front = last = mid = node;
            return;
        }
        front->prev = node;
        node->next = front;
        front = node;
        if(total%2==0)
            mid = mid->prev;
    }
    
    void pushMiddle(int val) {
        Node *node = new Node(val);
        total++;
        if(front==NULL)
        {
            front = last = mid = node;
            return;
        }
        node->next = mid;
        node->prev = mid->prev;
        mid->prev = node;
        if(node->prev)
            node->prev->next = node;
        if(front==mid)
        {
            front = node;
        }
        if(total%2==0)
            mid = node;
        else
        {
            int temp=node->data;
            node->data = mid->data;
            mid->data = temp;
        }
    }
    
    void pushBack(int val) {
        Node *node = new Node(val);
        total++;
        if(front==NULL)
        {
            front = mid = last = node;
            return;
        }
        last->next = node;
        node->prev = last;
        last=node;
        if(total%2==1)
            mid = mid->next;
    }
    
    int popFront() {
        if(front==NULL)
            return -1;
        total--;
        int data = front->data;
        if(total==0)
        {
            front = last = mid = NULL;
            return data;
        }
        if(total%2==1)
            mid=mid->next;
        front = front->next; 
        front->prev = NULL;
        return data;
    }
    
    int popMiddle() {
        if(front==NULL)
            return -1;
        total--;
        int data = mid->data;
        if(total==0)
        {
            front = mid = last = NULL;
            return data;
        } 
        Node *p,*n; 
        p=mid->prev;
        n=mid->next;
        if(p!=NULL)
            p->next = mid->next;
        n->prev = mid->prev;
        if(front==mid)
            front=n;
        if(total%2==1)
            mid = n;
        else
            mid = p;
        return data;
    }
    
    int popBack() {
        if(front==NULL)
            return -1;
        total--;
        int data = last->data;
        if(total==0)
        {
            front = last = mid = NULL;
            return data;
        }
        last = last->prev; 
        last->next = NULL;
        if(total%2==0)
            mid=mid->prev;
        return data;
    }
};
```
