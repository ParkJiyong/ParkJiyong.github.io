---
layout: post
title: "Python Product"
description: Made by PARKJIYONG in hanyang univ.
image: 'https://d81pi4yofp37g.cloudfront.net/wp-content/uploads/python-1.png'
category: 'Portfolio'
tags:
- ict
- python
- github
- portfolio
twitter_text: python Product
introduction: Product in the first year
---

Python team project
---
</br>
</br>

Pictures are needed to operate this code

</br>

***
**code below**


```
#_*_coding:utf_8_*_
##↑윗줄을 사용하면 한글을 사용할 수 있다.
# import함수를 통해 pygame과 sys를 불러온다.
import pygame, sys

#wall_reflect : 이름 그대로 벽에 튀기는 함수, 벽에 닿으면 ball의 변화량을 바꿔주는 함수이다.(주석1)
#이 함수에 아래에 닿을 경우 LIFE를 -1 하게 해보았다. 꺼지게도 해보려고 한다.
#실전에서는 모든 라이프가 달면 죽는 BGM과 재시작 버튼이 나오게 해야한다.
#reflect(반사)가 될 때에 튕기는 효과음이 필요하다.
def wall_reflect():
    global ball_change_x, ball_change_y,LIFE, Ilife, ball_x, ball_y
    global speed_count, down_count
    if ball_y < 0:
        ball_change_y = - ball_change_y

    if ball_x > 502:
        ball_change_x = - ball_change_x

    if ball_x < 0:
        ball_change_x = - ball_change_x

    if ball_y > 505:
        #life down
        LIFE -= 1
        #death
        if LIFE == 0:
           pygame.QUIT
           sys.exit()
        #ball을 다시 시작 지점으로 옮김
        ball_change_x = 0
        ball_change_y = 0
        speed_count = 0
        down_count = 3
        #임시 라이프 죽었을 때만 임시적으로 값을 가져, 다시 출발할 수 있게 한다.
        Ilife = 1
        text_create("You Died!", (100, 100))
        pygame.time.wait(500)
        #ball이 다시 옮겨짐
        ball_x = (10 - LIFE) * 50
        ball_y = 380

#block_reflect : 블럭에 닿으면 반사되는 코드이다. 위 함수와 마찬가지로 작동
### 참고 전역 변수(global) -- 함수 안의 변수는 독립된 변수이기 때문에 바깥의 변수와 연결해주는 다리 역할을 한다.
#마찬가지로 reflect(반사)될 시에 효과음이 필요하다.
#def block_reflect(x,y):

# moving : 이동을 구현하는 함수이다 / 효과음 필요한가?
def moving():
    global bar_x, x_change
    if event.type == pygame.KEYDOWN:
        if event.key == pygame.K_LEFT or event.key == pygame.K_a:
            x_change = - 30
        if event.key == pygame.K_RIGHT or event.key == pygame.K_d:
            x_change = + 30
    elif event.type ==  pygame.KEYUP:
        if event.key == pygame.K_UP or event.key == pygame.K_DOWN:
            x_change = 0

    bar_x = bar_x + x_change

# cnt_out : bar(움직이는 바)를 화면 밖으로 나가지 못하게 구동하는 코드이다.(주석2)
def cnt_out():
    global bar_x
    if 0 > bar_x:
        bar_x = 0
    elif 412 < bar_x:
        bar_x = 412
# bar에서 reflect되게 하는 함수이다. 아직 미완성이다. / 좌, 우에서 반사되는 코드가 필요하다.
# 어디가 문제인지를 잘 모르겠다.
def bar_reflect():
    global ball_change_y, bar_y, ball_change_x, speed_count,down_count
    global block_y_Line1_0, block_y_Line2_0, block_y_Line3_0, block_y_Line4_0
    global block_y_Line1_1, block_y_Line2_1, block_y_Line3_1 ,block_y_Line4_1
    global block_y_Line1_2, block_y_Line2_2, block_y_Line3_2, block_y_Line4_2
    global block_y_Line1_3, block_y_Line2_3, block_y_Line3_3, block_y_Line4_3
    if 400 < ball_y + 10 < 420 and bar_x < ball_x + 10 < bar_x + 110:
        ball_change_y = -ball_change_y
        speed_count += 1
        down_count -= 1
        if down_count == 0:
            block_y_Line1_0 += 70
            block_y_Line2_0 += 70
            block_y_Line3_0 += 70
            block_y_Line4_0 += 70
            block_y_Line1_1 += 70
            block_y_Line2_1 += 70
            block_y_Line3_1 += 70
            block_y_Line4_1 += 70
            block_y_Line1_2 += 70
            block_y_Line2_2 += 70
            block_y_Line3_2 += 70
            block_y_Line4_2 += 70
            block_y_Line1_3 += 70
            block_y_Line2_3 += 70
            block_y_Line3_3 += 70
            block_y_Line4_3 += 70

            down_count = 2
    elif ball_x+10 == bar_x and 400 < ball_y < 450 or ball_x == bar_x + 100 \
            and 400< ball_y <450:
        ball_change_x = -ball_change_x
#재미로 아이템을 넣어보았다. 아이템을 사용하면(space버튼) y축이 바뀌어 튕겨 날아간다.
## 개수 제한 10개
def speed_up():
    global speed_count, ball_change_y, ball_change_x
    if speed_count == 5:
        if ball_change_x < 0:
            ball_change_x = ball_change_x - 1
        else:
            ball_change_x = ball_change_x + 1
        ball_change_y = ball_change_y + 1
        speed_count = 0

def item():
    global ball_change_y, item_number
    if event.type == pygame.KEYDOWN:
        if event.key == pygame.K_SPACE and item_number > 0:
            ball_change_y = - ball_change_y
            item_number -= 1
#텍스트를 생성하는 함수이다.
def text_create(text,(x,y)):
    global font, Black
    text = font.render(text,True,Black)
    screen.blit(text,(x,y))

def ball_move():
    global ball_change_x, ball_change_y,Ilife
    if event.type == pygame.KEYDOWN:
        if event.key == pygame.K_r and Ilife == 1:
            ball_change_x = 3
            ball_change_y = 3.5
            Ilife -= 1
#앞으로 필요한 함수들을 정리해본다.

# start화면? --> 없어도 될 거 같기는 한데 구현하면 어떻게 해야할지 잘 모른다

#사용하지 않으면 일부 기능이 구동하지 않을 수 있다고 한다.
pygame.init()

#여러 가지 변수들이다. bar(캐릭터가 움직이는 막대), ball(팅겨지는 볼), block(부딪히면 사라지는) 등으로 구성된다.
#그 외 이미지를 불러오는 pygame함수들 --> (주석3)
White = (255,255,255)
Black = (0,0,0)
wid = 512
hei = 512
block_wid = 100
block_hei = 50
screen = pygame.display.set_mode((wid,hei))
pygame.display.set_caption("game")
bar = pygame.image.load("image_black.jpeg")
ball = pygame.image.load("image_red.jpeg")
bar = pygame.transform.scale(bar,(100,50))
ball = pygame.transform.scale(ball,(10,10))
block_yellow = pygame.image.load("image_yellow.jpeg")
block_yellow = pygame.transform.scale(block_yellow,(block_wid,block_hei))
block_blue = pygame.image.load("image_blue.png")
block_blue = pygame.transform.scale(block_blue,(block_wid,block_hei))
block_red = pygame.image.load("image_red.jpeg")
block_red = pygame.transform.scale(block_red,(block_wid,block_hei))
block2 = block_yellow
block3 = block_blue
block4 = block_red
block5 = block_yellow
block6 = block_blue
block7 = block_red
block8 = block_yellow
block9 = block_blue
block10 = block_red
block11 = block_yellow
block12 = block_blue
block13 = block_red
block14 = block_yellow
block15 = block_blue
block16 = block_red
#===========================================
block_y_Line1_0 = -140
block_y_Line2_0 = -140
block_y_Line3_0 = -140
block_y_Line4_0 = - 140
block_y_Line1_1 = -70
block_y_Line2_1 = -70
block_y_Line3_1 = -70
block_y_Line4_1 = -70
block_y_Line1_2 = 0
block_y_Line2_2 = 0
block_y_Line3_2 = 0
block_y_Line4_2 = 0
block_y_Line1_3 = 70
block_y_Line2_3 = 70
block_y_Line3_3 = 70
block_y_Line4_3 = 70

down_count = 2
block_x = 0
block_y = 0
bar_x = 10
bar_y = 400
ball_x = 10
ball_y = 380
x_change = 0
ball_change_x = 0
ball_change_y = 0
Ilife = 1
#item 개수 구현
item_number = 10
#font
font = pygame.font.Font(None,25)
LIFE = 10
speed_count = 0

#사실상 main함수의 역할을 하는 while문이다. 게임이 끝나기 전까지는 계속해서 돌아간다.
while True:
    # 만약 이벤트가 발생한다면 실행
    for event in pygame.event.get():
        # 게임 종료 함수
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        # 공을 화면 밖으로 못하게 하는 함수 + 이동함수
        moving()
        cnt_out()
        # item 반사형 아이템?
        item()
        # stop 멈추기
        ball_move()
        speed_up()
    # 이벤트가 발생하지 않아도 실행
    # ball의 움직임(change는 사실상 speed)
    ball_x = ball_x + ball_change_x
    ball_y = ball_y - ball_change_y

    # 실험 text 생성
    text_create("speed count" + str(abs(speed_count)),(0,450))
    text_create("down count" + str(down_count),(200,450))
    text_create("Life" + str(LIFE),(400,450))
    text_create("Speed" + str(ball_change_x),(0,400))
    # 공의 반사
    wall_reflect()

    bar_reflect()
    #game_over()
    # image 파일들을 화면에 나타내는 것.
    pygame.display.update()
    screen.fill(White)

    screen.blit(bar, (bar_x, bar_y))
    screen.blit(ball, (ball_x, ball_y))
    screen.blit(block_yellow,(10,block_y_Line1_0))
    screen.blit(block2,(10,block_y_Line1_1))
    screen.blit(block3,(10,block_y_Line1_2))
    screen.blit(block4,(10,block_y_Line1_3))
    screen.blit(block5,(140,block_y_Line2_0))
    screen.blit(block6,(140,block_y_Line2_1))
    screen.blit(block7,(140,block_y_Line2_2))
    screen.blit(block8,(140,block_y_Line2_3))
    screen.blit(block9,(280,block_y_Line3_0))
    screen.blit(block10,(280,block_y_Line3_1))
    screen.blit(block11,(280,block_y_Line3_2))
    screen.blit(block12,(280,block_y_Line3_3))
    screen.blit(block13,(410,block_y_Line4_0))
    screen.blit(block14,(410,block_y_Line4_1))
    screen.blit(block15,(410,block_y_Line4_2))
    screen.blit(block16,(410,block_y_Line4_3))

#1-3
    if 5 < ball_x < 115 and block_y_Line1_3 + 50 > ball_y > block_y_Line1_3 + 40:
        ball_change_y = -ball_change_y
        block_y_Line1_3 = -210
    if 5 < ball_x < 115 and block_y_Line1_3 < ball_y < block_y_Line1_3 + 10:
        ball_change_y = -ball_change_y
        block_y_Line1_3 = -210
    if 10 < ball_x + 5 < 20 and block_y_Line1_3 - 5 < ball_y < block_y_Line1_3 + 55:
        ball_change_x = -ball_change_x
        block_y_Line1_3 = -210
    if 50 < ball_x < 60 and block_y_Line1_3 - 5 < ball_y < block_y_Line1_3 + 55:
        ball_change_x = -ball_change_x
        block_y_Line1_3 = -210
#1-0
    if 5 < ball_x < 115 and block_y_Line1_0 + 50 > ball_y > block_y_Line1_0 + 40:
        ball_change_y = -ball_change_y
        block_y_Line1_0 = -210
    if 5 < ball_x < 115 and block_y_Line1_0 < ball_y < block_y_Line1_0 + 10:
        ball_change_y = -ball_change_y
        block_y_Line1_0 = -210
    if 10 < ball_x + 5 < 20 and block_y_Line1_0 - 5 < ball_y < block_y_Line1_0 + 55:
        ball_change_x = -ball_change_x
        block_y_Line1_0 = -210
    if 50 < ball_x < 60 and block_y_Line1_0 - 5 < ball_y < block_y_Line1_0 + 55:
        ball_change_x = -ball_change_x
        block_y_Line1_0 = -210

#1-1
    if 5 < ball_x < 115 and block_y_Line1_1 + 50 > ball_y > block_y_Line1_1 + 40:
        ball_change_y = -ball_change_y
        block_y_Line1_1 = -210
    if 5 < ball_x < 115 and block_y_Line1_1 < ball_y < block_y_Line1_1 + 10:
        ball_change_y = -ball_change_y
        block_y_Line1_1 = -210
    if 10 < ball_x + 5 < 20 and block_y_Line1_1 - 5 < ball_y < block_y_Line1_1 + 55:
        ball_change_x = -ball_change_x
        block_y_Line1_1 = -210
    if 50 < ball_x < 60 and block_y_Line1_1 - 5 < ball_y < block_y_Line1_1 + 55:
        ball_change_x = -ball_change_x
        block_y_Line1_1 = -210
#1-2
    if 5 < ball_x < 115 and block_y_Line1_2 + 50 > ball_y > block_y_Line1_2 + 40:
        ball_change_y = -ball_change_y
        block_y_Line1_2 = -210
    if 5 < ball_x < 115 and block_y_Line1_2 < ball_y < block_y_Line1_2 + 10:
        ball_change_y = -ball_change_y
        block_y_Line1_2 = -210
    if 10 < ball_x + 5 < 20 and block_y_Line1_2 - 5 < ball_y < block_y_Line1_2 + 55:
        ball_change_x = -ball_change_x
        block_y_Line1_2 = -210
    if 50 < ball_x < 60 and block_y_Line1_2 - 5 < ball_y < block_y_Line1_2 + 55:
        ball_change_x = -ball_change_x
        block_y_Line1_2 = -210

#2-0
    if 135 < ball_x < 245 and block_y_Line2_0 + 50 > ball_y > block_y_Line2_0 + 40:
        ball_change_y = -ball_change_y
        block_y_Line2_0 = -210
    if 135 < ball_x < 245 and block_y_Line2_0 < ball_y < block_y_Line2_0 + 10:
        ball_change_y = -ball_change_y
        block_y_Line2_0 = -210
    if 140 < ball_x + 5 < 150 and block_y_Line2_0 - 5 < ball_y < block_y_Line2_0 + 55:
        ball_change_x = -ball_change_x
        block_y_Line2_0 = -210
    if 180 < ball_x < 190 and block_y_Line2_0 - 5 < ball_y < block_y_Line2_0 + 55:
        ball_change_x = -ball_change_x
        block_y_Line2_0 = -210
#2-1
    if 135 < ball_x < 245 and block_y_Line2_1 + 50 > ball_y > block_y_Line2_1 + 40:
        ball_change_y = -ball_change_y
        block_y_Line2_1 = -210
    if 135 < ball_x < 245 and block_y_Line2_1 < ball_y < block_y_Line2_1 + 10:
        ball_change_y = -ball_change_y
        block_y_Line2_1 = -210
    if 140 < ball_x + 5 < 150 and block_y_Line2_1 - 5 < ball_y < block_y_Line2_1 + 55:
        ball_change_x = -ball_change_x
        block_y_Line2_1 = -210
    if 180 < ball_x < 190 and block_y_Line2_1 - 5 < ball_y < block_y_Line2_1 + 55:
        ball_change_x = -ball_change_x
        block_y_Line2_1 = -210
#2-2
    if 135 < ball_x < 245 and block_y_Line2_2 + 50 > ball_y > block_y_Line2_2 + 40:
        ball_change_y = -ball_change_y
        block_y_Line2_2 = -210
    if 135 < ball_x < 245 and block_y_Line2_2 < ball_y < block_y_Line2_2 + 10:
        ball_change_y = -ball_change_y
        block_y_Line2_2 = -210
    if 140 < ball_x + 5 < 150 and block_y_Line2_2 - 5 < ball_y < block_y_Line2_2 + 55:
        ball_change_x = -ball_change_x
        block_y_Line2_2 = -210
    if 180 < ball_x < 190 and block_y_Line2_2 - 5 < ball_y < block_y_Line2_2 + 55:
        ball_change_x = -ball_change_x
        block_y_Line2_2 = -210
#2-3
    if 135 < ball_x < 245 and block_y_Line2_3 + 50 > ball_y > block_y_Line2_3 + 40:
        ball_change_y = -ball_change_y
        block_y_Line2_3 = -210
    if 135 < ball_x < 245 and block_y_Line2_3 < ball_y < block_y_Line2_3 + 10:
        ball_change_y = -ball_change_y
        block_y_Line2_3 = -210
    if 140 < ball_x + 5 < 150 and block_y_Line2_3 - 5 < ball_y < block_y_Line2_3 + 55:
        ball_change_x = -ball_change_x
        block_y_Line2_3 = -210
    if 180 < ball_x < 190 and block_y_Line2_3 - 5 < ball_y < block_y_Line2_3 + 55:
        ball_change_x = -ball_change_x
        block_y_Line2_3 = -210

#3-0
    if 275 < ball_x < 385 and block_y_Line3_0 + 50 > ball_y > block_y_Line3_0 + 40:
        ball_change_y = -ball_change_y
        block_y_Line3_0 = -210
    if 275 < ball_x < 385 and block_y_Line3_0 < ball_y < block_y_Line3_0 + 10:
        ball_change_y = -ball_change_y
        block_y_Line3_0 = -210
    if 280 < ball_x + 5 < 290 and block_y_Line3_0 - 5 < ball_y < block_y_Line3_0 + 55:
        ball_change_x = -ball_change_x
        block_y_Line3_0 = -210
    if 320 < ball_x < 330 and block_y_Line3_0 - 5 < ball_y < block_y_Line3_0 + 55:
        ball_change_x = -ball_change_x
        block_y_Line3_0 = -210

#3-1
    if 275 < ball_x < 385 and block_y_Line3_1 + 50 > ball_y > block_y_Line3_1 + 40:
        ball_change_y = -ball_change_y
        block_y_Line3_1 = -210
    if 275 < ball_x < 385 and block_y_Line3_1 < ball_y < block_y_Line3_1 + 10:
        ball_change_y = -ball_change_y
        block_y_Line3_1 = -210
    if 280 < ball_x + 5 < 290 and block_y_Line3_1 - 5 < ball_y < block_y_Line3_1 + 55:
        ball_change_x = -ball_change_x
        block_y_Line3_1 = -210
    if 320 < ball_x < 330 and block_y_Line3_1 - 5 < ball_y < block_y_Line3_1 + 55:
        ball_change_x = -ball_change_x
        block_y_Line3_1 = -210
#3-2
    if 275 < ball_x < 385 and block_y_Line3_2 + 50 > ball_y > block_y_Line3_2 + 40:
        ball_change_y = -ball_change_y
        block_y_Line3_2 = -210
    if 275 < ball_x < 385 and block_y_Line3_2 < ball_y < block_y_Line3_2 + 10:
        ball_change_y = -ball_change_y
        block_y_Line3_2 = -210
    if 280 < ball_x + 5 < 290 and block_y_Line3_2 - 5 < ball_y < block_y_Line3_2 + 55:
        ball_change_x = -ball_change_x
        block_y_Line3_2 = -210
    if 320 < ball_x < 330 and block_y_Line3_2 - 5 < ball_y < block_y_Line3_2 + 55:
        ball_change_x = -ball_change_x
        block_y_Line3_2 = -210
#3-3
    if 275 < ball_x < 385 and block_y_Line3_3 + 50 > ball_y > block_y_Line3_3 + 40:
        ball_change_y = -ball_change_y
        block_y_Line3_3 = -210
    if 275 < ball_x < 385 and block_y_Line3_3 < ball_y < block_y_Line3_3 + 10:
        ball_change_y = -ball_change_y
        block_y_Line3_3 = -210
    if 280 < ball_x + 5 < 290 and block_y_Line3_3 - 5 < ball_y < block_y_Line3_3 + 55:
        ball_change_x = -ball_change_x
        block_y_Line3_3 = -210
    if 320 < ball_x < 330 and block_y_Line3_3 - 5 < ball_y < block_y_Line3_3 + 55:
        ball_change_x = -ball_change_x
        block_y_Line3_3 = -210
#4-0
    if 405 < ball_x < 515 and block_y_Line4_0 + 50 > ball_y > block_y_Line4_0 + 40:
        ball_change_y = -ball_change_y
        block_y_Line4_0 = -210
    if 405 < ball_x < 515 and block_y_Line4_0 < ball_y < block_y_Line4_0 + 10:
        ball_change_y = -ball_change_y
        block_y_Line4_0 = -210
    if 410 < ball_x + 5 < 420 and block_y_Line4_0 - 5 < ball_y < block_y_Line4_0 + 55:
        ball_change_x = -ball_change_x
        block_y_Line4_0 = -210
    if 450 < ball_x < 460 and block_y_Line4_0 - 5 < ball_y < block_y_Line4_0 + 55:
        ball_change_x = -ball_change_x
        block_y_Line4_0 = -210
#4-1
    if 405 < ball_x < 515 and block_y_Line4_1 + 50 > ball_y > block_y_Line4_1 + 40:
        ball_change_y = -ball_change_y
        block_y_Line4_1 = -210
    if 405 < ball_x < 515 and block_y_Line4_1 < ball_y < block_y_Line4_1 + 10:
        ball_change_y = -ball_change_y
        block_y_Line4_1 = -210
    if 410 < ball_x + 5 < 420 and block_y_Line4_1 - 5 < ball_y < block_y_Line4_1 + 55:
        ball_change_x = -ball_change_x
        block_y_Line4_1 = -210
    if 450 < ball_x < 460 and block_y_Line4_1 - 5 < ball_y < block_y_Line4_1 + 55:
        ball_change_x = -ball_change_x
        block_y_Line4_1 = -210
#4-2
    if 405 < ball_x < 515 and block_y_Line4_2 + 50 > ball_y > block_y_Line4_2 + 40:
        ball_change_y = -ball_change_y
        block_y_Line4_2 = -210
    if 405 < ball_x < 515 and block_y_Line4_2 < ball_y < block_y_Line4_2 + 10:
        ball_change_y = -ball_change_y
        block_y_Line4_2 = -210
    if 410 < ball_x + 5 < 420 and block_y_Line4_2 - 5 < ball_y < block_y_Line4_2 + 55:
        ball_change_x = -ball_change_x
        block_y_Line4_2 = -210
    if 450 < ball_x < 460 and block_y_Line4_2 - 5 < ball_y < block_y_Line4_2 + 55:
        ball_change_x = -ball_change_x
        block_y_Line4_2 = -210
#4-3
    if 405 < ball_x < 515 and block_y_Line4_3 + 50 > ball_y > block_y_Line4_3 + 40:
        ball_change_y = -ball_change_y
        block_y_Line4_3 = -210
    if 405 < ball_x < 515 and block_y_Line4_3 < ball_y < block_y_Line4_3 + 10:
        ball_change_y = -ball_change_y
        block_y_Line4_3 = -210
    if 410 < ball_x + 5 < 420 and block_y_Line4_3 - 5 < ball_y < block_y_Line4_3 + 55:
        ball_change_x = -ball_change_x
        block_y_Line4_3 = -210
    if 450 < ball_x < 460 and block_y_Line4_3 - 5 < ball_y < block_y_Line4_3 + 55:
        ball_change_x = -ball_change_x
        block_y_Line4_3 = -210

    if (block_y_Line1_0 or block_y_Line2_0 or block_y_Line3_0 or block_y_Line4_0 or block_y_Line1_1 or block_y_Line2_1 or
            block_y_Line3_1 or block_y_Line4_1 or block_y_Line1_2 or block_y_Line2_2 or block_y_Line3_2 or
            block_y_Line4_2 or block_y_Line1_3 or block_y_Line2_3 or block_y_Line3_3 or block_y_Line4_3) > 400:
        pygame.QUIT
        sys.exit()
```
