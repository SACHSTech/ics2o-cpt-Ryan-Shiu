Paste your current/final repl.it link here --> (https://repl.it/join/wlrqumef-shiuman)  
**Be sure it is shared with @EricFabroa**

# Pygame Workflow
![PygameLoop.png](PygameLoop.png)

'''
-------------------------------------------------------------------------------
Name:      main.py
Purpose:   Hockey game 

Author:    Shiu.R

Created:    07/01/2021
------------------------------------------------------------------------------
'''
""" 
A basic pygame template
"""
 
import pygame
 
# Define some colors
BLACK    = (   0,   0,   0)
WHITE    = ( 255, 255, 255)
GREEN    = (   0, 255,   0)
RED      = ( 255,   0,   0)
 
pygame.init()
  
# Set the width and height of the screen [width, height]
size = (800, 500)
screen = pygame.display.set_mode(size)
 
pygame.display.set_caption("My Game")
 
#Load graphics
#Backgrounds, achievements, and players
background_image = pygame.image.load("background.jpg").convert()
net_image = pygame.image.load("Ice-Hockey-Net.png").convert_alpha()
player_image = pygame.image.load("puck.png").convert_alpha()
contract_image = pygame.image.load("contract.png").convert_alpha()
all_star_image = pygame.image.load("all star.png").convert_alpha()
all_star_game_image = pygame.image.load("all star game.jpg").convert_alpha()
""""
target_image = pygame.image.load("target_image").convert_alpha()
"""
hat_trick_image = pygame.image.load("hat icon.webp").convert_alpha()
background_image2 = pygame.image.load("home.jpg").convert_alpha()
hat_trick_background_image = pygame.image.load("hat trick.webp").convert()
stanley_cup_background_image = pygame.image.load("stanley_cup_background.webp").convert()
stanley_cup_image = pygame.image.load("stanley cup.png").convert_alpha()
hockey_hall_of_fame_image = pygame.image.load("hockey hall of fame.png").convert_alpha()
hockey_hall_of_fame_background = pygame.image.load("hockey hall of fame.jpg")

#Buttons
home_button_image = pygame.image.load("home button.png").convert_alpha()
sponsor_image = pygame.image.load("sponsor.png").convert_alpha()
remove_image = pygame.image.load("remove.png").convert_alpha()

#Blank png images to swap into the loop
blank_image = pygame.image.load("Blank_image.png").convert_alpha()
blank2_image = pygame.image.load("Blank_image2.png").convert_alpha()
#Buttons for questions
true_button = pygame.image.load("true_button.png").convert_alpha()
false_button = pygame.image.load("false_button.webp").convert_alpha()
next_button = pygame.image.load("next.png").convert_alpha()



#Set positions of graphics
background_position = [0,7]
background_position2 = [34,10]
stanley_cup_background_position = [65,7]
hockey_hall_of_fame_background_position = [0,0]




#Variables for loop
score = 0
true_switch = 0
false_switch = 0
contract_switch = 0
double_points_switch = 0
sponsor_text_switch = 0
question_number = 1


#select the font, size, and italics
font = pygame.font.SysFont('Calibri', 18, True, False)
score_text = font.render(str(score) , True, WHITE)
#Blank text to swap for actual text
blank_text = font.render(" " , True , WHITE)
#Questions 
question_1 = font.render("Trojan is the least dangerous malware." , True , WHITE)
question_2 = font.render("Will this have an error?: print(''hi'')" , True , WHITE)
question_3 = font.render("Is 1 byte 8 bits?" , True ,WHITE)
question_4 = font.render("Do booleans use true and false?" , True, WHITE)
sponsor_text = font.render("Congratulations you have recieved a sponsorship from Malware inc. " , True , WHITE)
sponsor_text2 = font.render("Your clicks are now worth double. Answer questions to earn 50 points each" , True , WHITE)

blank_sponsor_text = font.render(" ", True, WHITE)
blank_sponsor_text2 = font.render(" ", True, WHITE)
blank_sponsor_text3 = font.render(" ", True, WHITE)
blank_sponsor_text4 = font.render(" ", True, WHITE)
answer_wrong = font.render("WRONG 0 points", True, WHITE)
answer_correct = font.render("CORRECT +50 points", True, WHITE)

# Possible answer text
answer = font.render(" ", True, WHITE)
answer_blank_text = font.render(" ", True, WHITE)
correct_text = font.render("CORRECT +50 points", True, WHITE)
wrong_text = font.render("WRONG 0 points", True, WHITE)

lost_achievements = font.render("Score under 10, lost achievements" , True ,  WHITE)


#Loop until the user clicks the close button.
done = False
button_appear = False

# Used to manage how fast the screen updates
clock = pygame.time.Clock()


#Initilize properties
net_x = 500
net_y = 250
contract_x = 50
contract_y = 400
all_star_x = 150
all_star_y = 400
hat_trick_x = 250
hat_trick_y = 400
stanley_cup_x = 350
stanley_cup_y = 400
sponsor_x = 450
sponsor_y = 400
hockey_hall_of_fame_x = 550
hockey_hall_of_fame_y = 400
home_button_x = 23
home_button_y = 1
questions_x = 740
questions_y = 1
blank_x = 300
blank_y = 100
blank2_x = 500
blank2_y = 100
next_x = 380
next_y = 100
remove_image_x = 300
remove_image_y = 230
#Size images
net_image = pygame.transform.scale(net_image, (250,150))
player_image = pygame.transform.scale(player_image, (25,25))
contract_image = pygame.transform.scale(contract_image, (75,75))
all_star_image = pygame.transform.scale(all_star_image, (75,75))
hat_trick_image = pygame.transform.scale(hat_trick_image, (75,75))
stanley_cup_image = pygame.transform.scale(stanley_cup_image, (75,75))
sponsor_image = pygame.transform.scale(sponsor_image, (75,75))
hockey_hall_of_fame_image = pygame.transform.scale(hockey_hall_of_fame_image, (125,85))
remove_image = pygame.transform.scale(remove_image, (50,50))
home_button_image = pygame.transform.scale(home_button_image, (50,50))
blank_image = pygame.transform.scale(blank_image, (25,25))
true_button = pygame.transform.scale(true_button, (25,25))
false_button = pygame.transform.scale(false_button, (25,25))
next_button = pygame.transform.scale(next_button, (90,60))

# -------- Main Program Loop -----------
while not done:
    # --- Main event loop
    pos = pygame.mouse.get_pos()
    for event in pygame.event.get(): # User did something
        if event.type == pygame.QUIT: # If user clicked close
            done = True # Flag that we are done so we exit this loop
        if event.type == pygame.MOUSEBUTTONDOWN:
          x = pos[0]
          y = pos[1]
          if x>530 and x<700 and y>245 and y<375:
           score = score + 100
           contract_switch = 1

          if contract_switch > 0 and score>=10 and x>0 and x<100 and y>385 and y<500:
            score = score + 25
            contract_switch = 0

          if score>25 and x>101 and x<201 and y>385 and y<500:
            background_image = all_star_game_image

          if x>1 and x<100 and y>1 and y <100:
            background_image = background_image2
            screen.blit(background_image2, background_position)

          if score >= 250 and x>225 and x<300 and y>400 and y<500:
            background_image = hat_trick_background_image
            screen.blit(hat_trick_background_image, background_position2)
          # Stanley Cup background
          if score >= 275 and x>325 and x<400 and y>400 and y<500:
            background_image = stanley_cup_background_image
            screen.blit(stanley_cup_background_image, stanley_cup_background_position)
        
          if score >= 300 and x>430 and x<505 and y>400 and y<500:
            blank_text = question_1
            blank_image = true_button
            blank2_image = false_button
            true_switch = 1
            false_switch = 1
            double_points_switch = 1
            blank_sponsor_text = sponsor_text
            blank_sponsor_text2 = sponsor_text2

          if double_points_switch == 1 and x>530 and x<700 and y>245 and y<375:
           score = score + 1

# for question 1
          if question_number == 1 and true_switch>0 and x>286 and x<314 and y>86 and y<114:
            score = score - 0
            answer = wrong_text
            true_switch = 0
            print("wrong1")

          if question_number == 1 and false_switch>0 and x>486 and x<514 and y>86 and y<114:
            score = score + 50

            answer = correct_text
            false_switch = 0
            print("correct1")

# for question 2            

          if question_number == 2 and true_switch>0 and x>286 and x<314 and y>86 and y<114:
            score = score - 0
            answer = wrong_text
            true_switch = 0
            print("wrong2")

          if question_number == 2 and false_switch>0 and x>486 and x<514 and y>86 and y<114:
            score = score + 50
            answer = correct_text
            false_switch = 0
            print("correct2")

# for question 3 
          if question_number == 3 and true_switch>0 and x>286 and x<314 and y>86 and y<114:
            score = score + 50
            answer = correct_text
            false_switch = 0
            print("correct3")

          if question_number == 3 and false_switch>0 and x>486 and x<514 and y>86 and y<114:
            score = score - 0
            answer = wrong_text
            true_switch = 0
            print("wrong3")

# for question 4
          if question_number == 4 and true_switch>0 and x>286 and x<314 and y>86 and y<114:
            score = score + 50
            answer = correct_text
            false_switch = 0
            print("correct3")

          if question_number == 4 and false_switch>0 and x>486 and x<514 and y>86 and y<114:
            score = score - 0
            answer = wrong_text
            true_switch = 0
            print("wrong3")




# for spnosor text
          if x>280 and x<330 and y>210 and y<265:
            blank_sponsor_text = sponsor_text
            sponsor_text = blank_sponsor_text3
            blank_sponsor_text2 = sponsor_text2
            sponsor_text2 = blank_sponsor_text4

#Next button for next question
          if x>365 and x<470 and y>90 and y<140:
            answer = answer_blank_text
            question_1 = blank_text
            blank_text = question_2
            question_2 = question_3
            question_3 = question_4
            true_switch = 1
            false_switch = 1
            question_number = question_number + 1
 


            #put rest of the questions here not after hockey hall of fame


            

          if score >= 500 and x>570 and x<630 and y>400 and y<500:
            background_image = hockey_hall_of_fame_background
            screen.blit(hockey_hall_of_fame_background, hockey_hall_of_fame_background_position)
            print("hello")


          
          
#Add answer questions to move on
  
    score_text = font.render(str(score) , True, WHITE)

    # --- Game logic should go here


     # Get the current mouse position. This returns the position
    # as a list of two numbers.
    player_position = pygame.mouse.get_pos()
    player_x = player_position[0]
    player_y = player_position[1]

    # First, clear the screen to white or whatever background colour. 
    # Don't put other drawing commands above this, or they will be erased with this command.
    """"
    screen.fill(WHITE)
    """
    # --- Drawing code should go here
     
    
    #Copy image here
    
    screen.blit(background_image, background_position)
    screen.blit(net_image, [net_x, net_y])
    screen.blit(home_button_image, [home_button_x, home_button_y])
    screen.blit(blank_image, [blank_x, blank_y])
    screen.blit(blank2_image, [blank2_x, blank2_y])
    screen.blit(player_image, [player_x, player_y])
    screen.blit(blank_text, [250,25])
    screen.blit(blank_sponsor_text, [1,175])
    screen.blit(blank_sponsor_text2, [1,205])
    screen.blit(answer, [250,50])
    if score >= 10:
      screen.blit(contract_image, [contract_x, contract_y])
      
    if score >= 100:
      screen.blit(all_star_image, [all_star_x, all_star_y])
    
    if score >= 250:
      screen.blit(hat_trick_image, [hat_trick_x, hat_trick_y])

    if score >= 275:
      screen.blit(stanley_cup_image, [stanley_cup_x, stanley_cup_y] )
    
    if score >= 300:
      screen.blit(sponsor_image, [sponsor_x, sponsor_y])
      screen.blit(remove_image, [remove_image_x, remove_image_y])
      screen.blit(next_button, [next_x, next_y])

    if score >= 500:
      screen.blit(hockey_hall_of_fame_image, [hockey_hall_of_fame_x, hockey_hall_of_fame_y] )
    
    screen.blit(player_image, [player_x, player_y])

   #Add text to screen
    screen.blit(score_text, [623, 230])

    # --- Go ahead and update the screen with what we've drawn.
    pygame.display.flip()
 
    # --- Limit to 60 frames per second
    clock.tick(60)
     
# Close the window and quit.
# If you forget this line, the program will 'hang'
# on exit if running from IDLE.
pygame.quit()
