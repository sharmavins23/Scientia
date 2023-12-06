Zobrist hashing is a [[Hash Function|hash function]] [[Algorithms|algorithm]] used in computer programs that play abstract games such as [[Chess]] in order to implement transposition tables, or lookup tables of board configurations.

For chess, the following algorithm is applied:

1. Construct a table of size $64\times 12$.
2. Set all positions $a, b$ of the table to $\text{table}[a][b] = \text{random bitstring}$.
3. Initialize $h = \text{random bitstring}$ if it is black's turn. If it is white's, $h=0$.
4. Iterate through the chessboard position indices $i$.
5. Get the piece value $j$ on the board - If empty, $j = 0$.
6. Compute $h = h \oplus \text{table}[i][j]$.
7. Repeat the loop from steps $4\to 7$ until no board squares remain.
