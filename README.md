# Ex.No: 4 Implementation of Alpha Beta Pruning
## DATE :24/02/24
## REGISTER NUMBER:212221040056
# AIM:
Write a Alpha beta pruning algorithm to find the optimal value of MAX Player from the given graph.
# Steps:
1. Start the program
2. Initially assign MAX and MIN value as 1000 and -1000.
3. Define the minimax function using alpha beta pruning
4. If maximum depth is reached then return the score value of leaf node. [depth taken as 3]
5. In Max player turn, assign the alpha value by finding the maximum value by calling the minmax 6. function recursively.
7. In Min player turn, assign beta value by finding the minimum value by calling the minmax
8. function recursively.
9. Specify the score value of leaf nodes and Call the minimax function.
10. Print the best value of Max player.
11. Stop the program.
```
DEVELOPED BY: HIBA RAJARAJESWARI
REG.NO: 212221040056
```
# PROGRAM:
```
class GraphNode:
    def __init__(self, value, children=[]):
        self.value = value
        self.children = children

def alpha_beta(node, alpha, beta, maximizing_player):
    if node is None:
        return None
    
    if len(node.children) == 0:
        return node.value
    
    if maximizing_player:
        value = float('-inf')
        for child in node.children:
            value = max(value, alpha_beta(child, alpha, beta, False))
            alpha = max(alpha, value)
            if alpha >= beta:
                break
        return value
    else:
        value = float('inf')
        for child in node.children:
            value = min(value, alpha_beta(child, alpha, beta, True))
            beta = min(beta, value)
            if alpha >= beta:
                break
        return value


node1 = GraphNode(3)
node2 = GraphNode(6)
node3 = GraphNode(2)
node4 = GraphNode(8)
node5 = GraphNode(2)
node6 = GraphNode(3)
node7 = GraphNode(5)
node8 = GraphNode(9)

node1.children = [node2, node3]
node2.children = [node4, node5]
node3.children = [node6, node7]
node4.children = [node8]

# Start alpha-beta pruning
optimal_value = alpha_beta(node1, float('-inf'), float('inf'), True)
print("Optimal value for MAX player:", optimal_value)

```
# OUTPUT:
![image](https://github.com/HibaRajarajeswari/Alpha-Beta-Pruning/assets/129970809/d7716218-363f-49c1-8b20-2fc4fc63551d)
# RESULT:
Thus the best score of max player was found using Alpha Beta Pruning.
