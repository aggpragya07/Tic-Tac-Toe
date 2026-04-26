# Tic-Tac-Toe
Basic Tic-Tac-Toe game
#tic-tac-toe

#Step 1 : Board Setup

board=[" "]*9
current_player="X"#initiated current player
    #" "=empty box
    #*9=repeat 9 times

    #step2:print board
def print_board():
    print(board[0],"|",board[1],"|",board[2])
    print("-----------")
    print(board[3],"|",board[4],"|",board[5])
    print("-----------")
    print(board[6],"|",board[7],"|",board[8])
    print("-----------")
  
  #function to check if player is won  
def check_winner(player):
    #all possible winning combinations(rows,columns,diagonals)
    win_positions=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]]
    
    #check each winning combinations
    for pos in win_positions:
        #if all 3 positions have the same players symbol->win
        if board[pos[0]]==board[pos[1]]==board[pos[2]]==player:
            return True
            
    return False#no winning condition met
            
#function to check if game is a draw        
def check_draw():
    #if no empty space is left->its a draw
    return " " not in board
#game introduction  
print("Welcome to Tic-Tac-Toe!")
print("Player X starts first")
print("Choose a position from 1 to 9")
#loop to call the function and move ahead in our game
while True:
    move=input("Player "+current_player +",enter position(1-9):")
    
    
    #Check if input is a number 
    if not move.isdigit():
        print("Please enter a number only ")
        continue #Restart loop
    
    move=int(move)
    
    #Check if input is within valid range 
    if move<1 or move>9:
        print("Invalid position!Choose from 1 to 9 ")
        continue 
    
    index=move-1  #Convert to list index(0-based)


    #Check if the position is already filled 
    if board[index]!=" ":
        print("This posiiton is already taken.try again")
        continue
    
    #place the player's symbol on the board
    board[index]=current_player
    
    #check if the current player win 
    if check_winner(current_player):
        print_board()
        print("Player",current_player,"wins!")
        break
    #check for draw
    if check_draw():
        print_board()
        print("its a draw")
        break
    #switch player
    if current_player=="X":
        current_player="O"
        
    else:
        current_player="X"