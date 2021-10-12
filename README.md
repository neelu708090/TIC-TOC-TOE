# TIC-TOC-TOE
Step 1- A board to display the player.

from IPython.display import clear_output
def display_board(board):
    clear_output()
    print('   |   | ')
    print(' '+board[7]+' | '+board[8]+' | '+board[9])
    print('   |   | ')
    print('-----------')
    print('   |   | ')
    print(' '+board[4]+' | '+board[5]+' | '+board[6])
    print('   |   | ')
    print('-----------')
    print('   |   | ')
    print(' '+board[1]+' | '+board[2]+' | '+board[3])
    print('   |   | ')
sample_board=[' ']*10 display_board(sample_board)

Step 2- Function to take input from the player.

def player_input():
    #A EMPTY VARIABLE OF STR DATATYPE.
    marker=''
    #while loop is running till the condition is false.
    while marker!='X' and marker!='O':
        marker=input('Player 1 choose X or O: ').upper()
        player1=marker
        
        if player1=='X':
            player2='O'
        else:
            player2='X'
    return(player1,player2)
#Tuple Unpacking. player1_value,player2_value=player_input()

player1_value=X

def place_marker(board,marker,position):
    board[position]=marker
player2_value=O

def win_check(board,mark):
    
    return ((board[7] == mark and board[8] == mark and board[9] == mark) or # across the top
    (board[4] == mark and board[5] == mark and board[6] == mark) or # across the middle
    (board[1] == mark and board[2] == mark and board[3] == mark) or # across the bottom
    (board[7] == mark and board[4] == mark and board[1] == mark) or # down the middle
    (board[8] == mark and board[5] == mark and board[2] == mark) or # down the middle
    (board[9] == mark and board[6] == mark and board[3] == mark) or # down the right side
    (board[7] == mark and board[5] == mark and board[3] == mark) or # diagonal
    (board[9] == mark and board[5] == mark and board[1] == mark)) # diagonal
import random
def choose_first():
    if random.randint(0,1)==0:
        return'Player 2'
    else:
        return 'Player 1'
    
def space_check(board,position):
    return board[position]==' '
space_check(sample_board,9)

def full_board_check(board):
    for i in range(1,10):
        if space_check(board,i):
            return False
    return True
full_board_check(sample_board)

def player_choice(board):
    position=0
    while position not in [1,2,3,4,5,6,7,8,9] or not space_check(board,position):
        position=int(input('Chooseyour next position:(1-9) '))
        return position
def replay():
    return input('Do you want to play again? Enter Yes or No.').lower().startswith('y')
replay()

#Start the game
print('Welcome to TIC TOC TOE! ')
#take a while loop till True.
while True:
    #Reset the board.
    #make a list as board.
    
    the_board=[' ']*10
    
    #take the input from the player call the input function.
    
    player1_marker,player2_marker=player_input()
    
    #make a variable turn in which the value of player who play first is stored using random choose_first function.
    turn=choose_first()
    
    print(turn+' will go first. ')
    
    #make a variable play_game that is taking input from the player to start the game.
    
    play_game=input('Are you ready to play? Enter Yes or No. ')
    #condition
    if play_game =='Yes':
     #a varaible game_on stores the value True or False to start the game.
        game_on= True
    else:
        game_on=False
    #start a loop till the game_on is True.
    while game_on:
        if turn=='Player 1':
        # Player 1 turn.
        # Display the board to show the Player.Call the display_board function.
            display_board(the_board)
        #call the function player_choice and return the position.
            position=player_choice(the_board)
        #return the index value where the player want to fill X or O.
            place_marker(the_board,player1_marker,position)
            if win_check(the_board,player1_marker):
                display_board(the_board)
                print('Player 1 has won! ')
                game_on=False
            else:
                if full_board_check(the_board):
                    display_board(the_board)
                    print('Game Tied!. ')
                    break
                else:
                    turn='Player 2'
        else:
            display_board(the_board)
        #call the function player_choice and return the position.
            position=player_choice(the_board)
        #return the index value where the player want to fill X or O.
            place_marker(the_board,player2_marker,position)
            if win_check(the_board,player2_marker):
                display_board(the_board)
                print('Player 2 has won! ')
                game_on=False
            else:
                if full_board_check(the_board):
                    display_board(the_board)
                    print('Game Tied!. ')
                    break
                else:
                    turn='Player 1'
    if not replay():
        break
            
        
        
    
   |   | 
 X |   | O
   |   | 
-----------
   |   | 
   | X | O
   |   | 
-----------
   |   | 
 O | X | O
   |   | 
Player 2 has won! 
Do you want to play again? Enter Yes or No.No
