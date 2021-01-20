# Little-Birdie
#Hit the clouds to gain points and win the game! If little birdie hits the helicopter three times then you lose:(
# Python Code



#!/bin/python3
import turtle
import random
import math


# set up screen with
# 500 x 500 dimensions
# image
screen = turtle.Screen()
s_length = 500
s_width = 500
screen = turtle.Screen()
screen.setup(s_length, s_width)
screen.bgpic("Sky.jpg")
screen.tracer(0)

#set welcome screen
# w = turtle.Turtle()
# w.speed(0)
# w.shape("square")
# w.color("black")
# w.penup()
# w.hideturtle()
# w.goto(0, 10)
# w.write("Welcome to Little Birdie!", align="center", font=("arial", 30,"normal"))
# w.goto(0, -30)
# w.write("Press Enter to Play", align="center", font=("arial", 30,"normal"))
# w.tracer(0)

#Print title of the game
#print "Welcome to Little Birdie!!!"
#print "You will get 3 lives! Hit a helicopter and you will die! Get a score of 50 hitting the clouds to win:)"




  # random postion of the characters on the y-axis
def random_y_pos():
  starting_pos = random.randint(-220, 220)
  return starting_pos
  
  # starting position of the characters on the x-axis
  start_x_pos = 280

#Dictionaries
helicopter = {"turtle": turtle.Turtle(), "radius":20, "speed":150, "shape": "Dr.pepper.png"};
bird = {"turtle": turtle.Turtle(), "radius":50, "speed":100,"shape": "Birdie.png",};
cloud = {"turtle": turtle.Turtle(), "radius":10, "speed":100,"shape": "cloud.png"};
cloud_2 = {"turtle": turtle.Turtle(), "radius":30, "speed":100,"shape": "Cloud 2 (1).png"};

#Add Helicopter
screen.addshape(helicopter["shape"])
helicopter["turtle"].shape(helicopter["shape"])
helicopter["turtle"].penup()
helicopter["turtle"].goto(-90,120)
helicopter["turtle"].tracer(0)

#Add bird
screen.addshape(bird["shape"])
bird["turtle"].shape(bird["shape"])
# set up a player to beginning of screen
screen.addshape(bird["shape"])
bird["turtle"].shape(bird["shape"])
bird["turtle"].penup()
bird["turtle"].left(90)
bird["turtle"].goto(-200,30)
bird["turtle"].tracer(0)

#Add cloud
screen.addshape(cloud["shape"])
cloud["turtle"].shape(cloud["shape"])
#Move cloud to specific part of screen
cloud["turtle"].penup()
cloud["turtle"].goto(20,190)
cloud["turtle"].tracer(0)

#Add cloud 2
screen.addshape(cloud_2["shape"])
cloud_2["turtle"].shape(cloud_2["shape"])
cloud_2["turtle"].penup()
cloud_2["turtle"].goto(50,-15)
cloud_2["turtle"].tracer(0)

#set up the values of scores and lives 
bird["scores"] = 0
bird["lives"] = 3

#set up turtle to write scores and lives
pen = turtle.Turtle()

#function for drawing scores and lives
pen.hideturtle()
pen.penup()
pen.goto(150,200)
pen.write("Scores: " + str(bird["scores"]), move=False, align='left', font=('Arial', 15, 'normal'))
pen.goto(150,225)
pen.write("Lives: " + str(bird["lives"]), move=False, align='left', font=('Arial', 15, 'normal'))


# Main Function
def main():
  welcome.clear()
  scores = 0
  lives = 3
  scoring = 10
  start_x_pos = 100
  pen = turtle.Turtle()
  pen.speed(0)
  pen.shape("square")
  pen.color("white")
  pen.penup()
  pen.hideturtle()
  pen.goto(0, 233)
  pen.write("score: {}    lives: {}".format(bird["scores"], lives), align="center", font=("arial", 15,"normal"))
  pen2 = turtle.Turtle()
  pen1 = turtle.Turtle()


# distance between the player and the characters
dis_amount = 30
  
# boundary of the characters changes on the -x-axis
ending_x_pos = -280

#Add up/down keys
def up():
  bird["turtle"].clear()
  if bird["turtle"].ycor() <= 225:
    current_y = bird["turtle"].ycor()
    new_y = current_y + 10
    bird["turtle"].sety(new_y)
  
def down():
 bird["turtle"].clear()
 if bird["turtle"].ycor() >= -225:
    current_y = bird["turtle"].ycor()
    new_y = current_y - 10
    bird["turtle"].sety(new_y)

  
screen.onkey(up, "up")
screen.onkey(down, "down")
screen.listen()


#Implement Collision detection 

def are_colliding(obj_1, obj_2):
  dx = obj_1["turtle"].xcor() - obj_2["turtle"].xcor()
  dy = obj_1["turtle"].ycor() - obj_2["turtle"].ycor()
  distance = math.sqrt(dx * dx + dy * dy)
    
  if distance < obj_1['radius'] + obj_2['radius']:
    collision_detected = True
    return collision_detected 



# create the animation of characters
# main loop
def main():
  running = True
  
  while (running):
    x = random.randrange(-250,250)
    y = random.randrange(-230,230)
      
  # create the animation of characters
  
   #Animation for cloud
    cloud["turtle"].showturtle()
    cloud["turtle"].clear()
    cloud["turtle"].setx(cloud["turtle"].xcor() - 20 )
    if (cloud["turtle"].xcor() <= (-s_width/2) - cloud["radius"]):  # make the cloud come back
      cloud["turtle"].hideturtle()
      cloud["turtle"].setx(s_width/2 + cloud["radius"])
      cloud["turtle"].sety(y)
    cloud["turtle"].update()
  
  
  #Animation for helicopter
    helicopter["turtle"].showturtle()
    helicopter["turtle"].clear()
    helicopter["turtle"].setx(helicopter["turtle"].xcor() - 28)
    if (helicopter["turtle"].xcor() <= (-s_width/2) - helicopter["radius"]):  # make the helicopter come back
      helicopter["turtle"].hideturtle()
      helicopter["turtle"].setx(s_width/2 + helicopter["radius"])
      helicopter["turtle"].sety(y)
    helicopter["turtle"].update()  
  
  
  #Animation for cloud 2
    #start_x_pos = 100
    #scoring = 10
    
    cloud_2["turtle"].showturtle()
    cloud_2["turtle"].clear()
    cloud_2["turtle"].setx(cloud_2["turtle"].xcor() - 18)
    if (cloud_2["turtle"].xcor() <= (-s_width/2) - cloud_2["radius"]):  # make the cloud come back
      cloud_2["turtle"].hideturtle()
      cloud_2["turtle"].setx(s_width/2 + cloud_2["radius"])
      cloud_2["turtle"].sety(y)
    cloud_2["turtle"].update()
  
  
  # test if the player is colliding with the cloud benefit charachter
    if are_colliding(bird, cloud):
      bird["scores"] += 10
      cloud["turtle"].setpos(250,y)
      pen.clear()
      pen.update()
    
      pen.goto(150,200)
      pen.write("Scores: " + str(bird["scores"]), move=False, align='left', font=('Arial', 15, 'normal'))
      pen.goto(150,225)
      pen.write("Lives: " + str(bird["lives"]), move=False, align='left', font=('Arial', 15, 'normal'))
    
        
      # test if the player is colliding with the cloud 2 benefit charachter
    elif are_colliding(bird, cloud_2):
      bird["scores"] += 10
      cloud_2["turtle"].setpos(250,y)
      pen.clear()
      pen.update()
      pen.goto(150,200)
      pen.write("Scores: " + str(bird["scores"]), move=False, align='left', font=('Arial', 15, 'normal'))
      pen.goto(150,225)
      pen.write("Lives: " + str(bird["lives"]), move=False, align='left', font=('Arial', 15, 'normal'))
  
      # test if the player is colliding with the helicopter harm charachter
    elif are_colliding(bird, helicopter):
      bird["lives"] -= 1
      helicopter["turtle"].setpos(250,y)
      pen.clear()
      pen.update()
      pen.goto(150,200)
      pen.write("Scores: " + str(bird["scores"]), move=False, align='left', font=('Arial', 15, 'normal'))
      pen.goto(150,225)
      pen.write("Lives: " + str(bird["lives"]), move=False, align='left', font=('Arial', 15, 'normal'))
  
  # stop looping when lives is 0
    
    elif bird["lives"] == 0:
      running = False
      bird["turtle"].hideturtle()
      cloud["turtle"].hideturtle()
      cloud_2["turtle"].hideturtle()
      helicopter["turtle"].hideturtle()
      
  #Gameover screen
  
    # display a gameover screen when it is game over
  
      pen2 = turtle.Turtle()
      pen2.hideturtle()
      pen2.write("Game Over!", move=False, align='center', font=('Arial', 40, 'normal'))
      
    
  # Display Winning screen
    elif bird["scores"] == 100: 
      running = False
      bird["turtle"].hideturtle()
      cloud["turtle"].hideturtle()
      cloud_2["turtle"].hideturtle()
      helicopter["turtle"].hideturtle()
      win = turtle.Turtle()
      win.hideturtle()
      win.write("You Win!", move=False, align='center', font=('Arial', 40, 'normal'))
      
      
    screen.update()

main()


