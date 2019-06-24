# development-of-graphic-applications
import turtle
import random
import math

turtle.ht()
turtle.speed(-10)
turtle.title("Игра русская рулетка")

def circle(start_point,color,radius):
    turtle.pencolor(color)
    turtle.penup()
    turtle.goto(start_point)
    turtle.pendown()
    turtle.fillcolor(color)
    turtle.begin_fill()
    turtle.circle(r)
    turtle.end_fill()
    
turtle.speed(0)

def draw_pistol(base_x, base_y):
   #основной круг
   gotoxy(base_x, base_y)
   turtle.circle(80)
   #мушка
   gotoxy(base_x, base_y+160)
   draw_circle(5, "red")
 
    #барабан
   for i in range(0,7):
      phi_rad = PHI * i * math.pi / 180.0
      gotoxy(base_x+math.sin(phi_rad)*R, math.cos(phi_rad)*R + 60)
      draw_circle(22, "white")
                                           #circle((math.sin(fpi_rad)*r, math.cos(fpi_rad)*r),color,50)
def rotate_pistol(base_x, base_y, start):
   for i in range(start,random.randrange(7,100)):
      phi_rad = phi * i * math.pi / 180.0
      gotoxy(base_x+math.sin(phi_rad)*r, math.cos(phi_rad)*r + 60)
      draw_circle(22, "brown")
      draw_circle(22, "white")

   gotoxy(math.sin(phi_rad)*r, math.cos(phi_rad)*r + 60)
   draw_circle(22, "brown")

draw_pistol(100,100)                                           

phi = 360 / 7
answer = ''
start = 0
cnt = 0
r = 120
lost = 0

baraban_empty()

while answer != 'N':
    answer = turtle.textinput('Играем?','Y/N')
    if lost != 0:
        turtle.undo() #Очищаем строку вы проиграли через буфер черепахи
    if answer.lower() == 'y':
        for i in range(start,random.randrange(7,14)):
            fpi_rad = phi * i * math.pi / 180
            color = 'yellow'
            circle((math.sin(fpi_rad)*r, math.cos(fpi_rad)*r),color,50)
            if i == 0:
                turtle.resizemode("auto")
                turtle.textinput('Револьвер заряжен!','Крутим? Y/N')
            color = 'white'
            circle((math.sin(fpi_rad)*r, math.cos(fpi_rad)*r),color,50)
        color = 'yellow'
        circle((math.sin(fpi_rad)*r, math.cos(fpi_rad)*r),color,50)
        start = i % 7
    if start == 0 and answer.lower() == 'y':
        turtle.penup()
        turtle.goto(0,-180)
        turtle.pencolor('red')
        turtle.write('Вы проиграли!',font=('Arial',28,'underline'),align='center')
        lost = 1
        #turtle.exitonclick() #Выход по клику на экране
    else:
        pass
