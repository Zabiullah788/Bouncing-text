# Bouncing-text
import pygame
import sys

text = input("Enter any text: ")

pygame.init()
width, height = 800, 600
screen = pygame.display.set_mode((width,height))
pygame.display.set_caption("Bouncing Text")

font = pygame.font.SysFont("Arial",48)
text = font.render(text, True, (255,255,255))
text_react= text.get_rect(center = (width // 2, height // 2))

x_speed , y_speed = 5,5
clock = pygame.time.Clock()

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    screen.fill((0, 0, 0))
    text_react.x += x_speed
    text_react.y += y_speed

    if text_react.left < 0 or text_react.right > width:
        x_speed = -x_speed
    if text_react.top < 0 or text_react.bottom > height:
        y_speed = -y_speed

    screen.blit(text, text_react)
    pygame.display.flip()
    clock.tick(60)
