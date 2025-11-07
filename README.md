# simple_circle_game
This is a small interactive game created using Python + Pygame.  A ball is displayed in the center of the screen.  When the user clicks on the ball, it increases in size.  The ball keeps growing based on user interactions.  This project is great for beginners learning Pygame, event handling, mouse click detection, and basic game loops.
import pygame
import sys
import math

pygame.init()

# Window
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Ball Growth Game")

# Ball data
radius = 50
ball_x, ball_y = WIDTH // 2, HEIGHT // 2
ball_color = (255, 0, 0)

clock = pygame.time.Clock()
running = True

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

        if event.type == pygame.MOUSEBUTTONDOWN:
            mouse_x, mouse_y = pygame.mouse.get_pos()

            # distance formula
            distance = math.sqrt((mouse_x - ball_x) ** 2 + (mouse_y - ball_y) ** 2)

            if distance <= radius:
                radius += 10  # increase size

    screen.fill((255, 255, 255))
    pygame.draw.circle(screen, ball_color, (ball_x, ball_y), radius)
    pygame.display.update()
    clock.tick(60)

pygame.quit()
sys.exit()
