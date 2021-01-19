Paste your current/final repl.it link here --> (https://repl.it/join/wabbayfp-shiuman)  
**Be sure it is shared with @EricFabroa**

# Pygame Workflow
![PygameLoop.png](PygameLoop.png)

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
background_image = pygame.image.load("background.jpg").convert()
net_image = pygame.image.load("Ice-Hockey-Net.png").convert_alpha()
player_image = pygame.image.load("puck.png").convert_alpha()
contract_image = pygame.image.load("contract.png").convert_alpha()
#Set positions of graphics
background_position = [0,7]

#Variables for loop
score = 0

#select the font, size, and italics
font = pygame.font.SysFont('Calibri', 18, True, False)
""""
score_text = font.render(str(score) , True, WHITE)
"""
#Loop until the user clicks the close button.
done = False
 
# Used to manage how fast the screen updates
clock = pygame.time.Clock()

#Initilize box properties
net_x = 500
net_y = 250
"""
net_width = 75
net_height = 75
"""
contract_x = 50
contract_y = 400

#Size images
net_image = pygame.transform.scale(net_image, (250,150))
player_image = pygame.transform.scale(player_image, (25,25))
contract_image = pygame.transform.scale(contract_image, (75,75))

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
            score = score + 1
        if event.type == pygame.MOUSEBUTTONDOWN:
          

  
    score_text = font.render(str(score) , True, WHITE)
  

    # --- Game logic should go here


     # Get the current mouse position. This returns the position
    # as a list of two numbers.
    player_position = pygame.mouse.get_pos()
    player_x = player_position[0]
    player_y = player_position[1]

    # First, clear the screen to white or whatever background colour. 
    # Don't put other drawing commands above this, or they will be erased with this command.
    screen.fill(WHITE)
 
    # --- Drawing code should go here
     
    
    #Copy image here
    
    screen.blit(background_image, background_position)
    screen.blit(net_image, [net_x, net_y])
    screen.blit(player_image, [player_x, player_y])
    screen.blit(contract_image, [contract_x, contract_y])
   
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
