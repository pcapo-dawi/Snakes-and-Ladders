# Snakes-and-Ladders
codewars 5 kyu
# Introduction
Snakes and Ladders is an ancient Indian board game regarded today as a worldwide classic. It is played between two or more players on a gameboard having numbered, gridded squares. A number of "ladders" and "snakes" are pictured on the board, each connecting two specific board squares.
# Task
Your task is to make a simple class called SnakesLadders. The test cases will call the method play(die1, die2) independantly of the state of the game or the player turn. The variables die1 and die2 are the die thrown in a turn and are both integers between 1 and 6. The player will move the sum of die1 and die2.
# The Board
![snakesandladdersboard](https://github.com/pcapo-dawi/Snakes-and-Ladders/assets/146750011/d0737231-6c12-4335-823d-006ae67ec988)

# Rules
1.  There are two players and both start off the board on square 0.

2.  Player 1 starts and alternates with player 2.

3.  You follow the numbers up the board in order 1=>100

4.  If the value of both die are the same then that player will have another go.

5.  Climb up ladders. The ladders on the game board allow you to move upwards and get ahead faster. If you land exactly on a square that shows an image of the bottom of a ladder, then you may move the player all the way up to the square at the top of the ladder. (even if you roll a double).

6.  Slide down snakes. Snakes move you back on the board because you have to slide down them. If you land exactly at the top of a snake, slide move the player all the way to the square at the bottom of the snake or chute. (even if you roll a double).

7.  Land exactly on the last square to win. The first person to reach the highest square on the board wins. But there's a twist! If you roll too high, your player "bounces" off the last square and moves back. You can only win by rolling the exact number needed to land on the last square. For example, if you are on square 98 and roll a five, move your game piece to 100 (two moves), then "bounce" back to 99, 98, 97 (three, four then five moves.)

8.  If the Player rolled a double and lands on the finish square “100” without any remaining moves then the Player wins the game and does not have to roll again.
# Returns
Return Player n Wins!. Where n is winning player that has landed on square 100 without any remainding moves left.

Return Game over! if a player has won and another player tries to play.

Otherwise return Player n is on square x. Where n is the current player and x is the sqaure they are currently on.
## Code
````
public class SnakesLadders {
    static int[] jugadores = new int[]{0,0};
    static int jugador = 0;
    static boolean terminado = false;
    static int[] tablero = new int[] {0,1,38,3,4,5,6,14,31,9,10,11,12,13,14,26,6,17,18,19,20,42,22,23,24,25,26,27,84,29,30,31,32,33,34,35,44,37,38,39,40,41,42,43,44,45,25,47,48,11,50,67,52,53,54,55,56,57,58,59,60,61,19,63,60,65,66,67,68,69,70,91,72,73,53,75,76,77,98,79,80,81,82,83,84,85,86,94,88,68,90,91,88,93,94,75,96,97,98,80,100}; 
    public SnakesLadders() {
      jugador = 0;
      jugadores[0] = 0;
      jugadores[1] = 0;
      terminado = false;
    }
    public String play(int die1, int die2) {
        if(terminado) return "Game over!";
            String ret = "";
            jugadores[jugador] += die1 + die2;
            if(jugadores[jugador] > 100) jugadores[jugador] = 200-jugadores[jugador];
            jugadores[jugador] = tablero[jugadores[jugador]];
            ret = "Player "+(jugador+1)+" is on square "+jugadores[jugador];
            if(jugadores[jugador] == 100){
              ret = "Player "+(jugador+1)+" Wins!";
              terminado = true;
            }
            if(die1 != die2){
                jugador = 1-jugador;
            }      
            return ret;
    }
}
