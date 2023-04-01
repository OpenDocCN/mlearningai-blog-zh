# 人工智能学习玩 Flappy 鸟游戏-有趣的项目-与源代码

> 原文：<https://medium.com/mlearning-ai/ai-learns-to-play-flappy-bird-game-fun-project-with-source-code-22250fd4cabf?source=collection_archive---------6----------------------->

因此，在今天的博客中，我们将实现由人工智能玩的 Flappy Bird 游戏。我们将通过使用代表 [***的**整洁**来实现这一点。*** 每个机器学习工程师的一大幻想就是做出一个可以自己学习玩的游戏。在今天的博客中，我们将看到我们如何做到这一点。所以不浪费任何时间…](https://neat-python.readthedocs.io/en/latest/)

**在这里阅读带源代码的整篇文章—**[https://machine learning projects . net/ai-learning-to-play-flappy-bird-game/](https://machinelearningprojects.net/ai-learns-to-play-flappy-bird-game/)

![](img/5de50fc32e853ccf06793fc7d7ff91ee.png)

AI plays Flappy bird game

# 让我们开始吧…

我们将主要需要以下两个库来实现这一点:

*   pygame
*   整洁的蟒蛇皮

## Flappy Bird 游戏的代码…

```
import pygame
import neat
import os
import random

pygame.font.init()  # some initialization to use font in pygame

WIN_HEIGHT = 800
WIN_WIDTH = 500
DRAW_LINES = True
GEN = 0  # declaring generation variable

pygame.display.set_caption("Flappy Bird")

# importing the images of birds, pipes, background and base
BIRD_IMGS = [pygame.transform.scale2x(pygame.image.load('imgs\\bird1.png')),
             pygame.transform.scale2x(pygame.image.load('imgs\\bird2.png')),
             pygame.transform.scale2x(pygame.image.load('imgs\\bird3.png'))]
BASE_IMG = pygame.transform.scale2x(pygame.image.load('imgs\\base.png'))
BG_IMG = pygame.transform.scale2x(pygame.image.load('imgs\\bg1.png'))
PIPE_IMG = pygame.transform.scale2x(pygame.image.load('imgs\\pipe.png'))

# declaring font
STAT_FONT = pygame.font.SysFont('comicsans', 50)

# CLASS BIRD
class Bird:
    ROTATION_VEL = 20
    MAX_ROTATION = 25
    ANIMATION_TIME = 5
    IMGS = BIRD_IMGS

    def __init__(self, x, y):  # constructor for class bird
        self.x = x
        self.y = y
        self.height = self.y
        self.frame_count = 0
        self.tilt = 0
        self.vel = 0
        self.img_number = 0  # image in which the bird's wings are upwards
        self.img = self.IMGS[0]  # image in which the bird's wings are upwards

    def jump(self):
        self.vel = -10.5  # negative velocity refers to jump upwards
        self.frame_count = 0  # reset the frames
        self.height = self.y  # reset the height

    def move(self):
        self.frame_count += 1  # update the frames when the bird moves
        # d > 0 means downwards and d<0 means upwards and same for velocity also
        # and also bird is just moving in y direction and not in x direction
        d = self.vel * self.frame_count + 1.5 * self.frame_count ** 2  # frame count also works as time
        if d >= 16: # if the bird is falling and it falls more than 16 pixels then stop falling and face straight moving
            d = 16
        # if d < 0:   # just for tuning so that upward movement is seen clear
        #     d -= 2

        self.y = self.y + d

        if d < 0 or self.y < self.height + 50:  # (d<0) this is the case when when bird is going upward
            if self.tilt < self.MAX_ROTATION:  # so making a tilt angle of max rotation
                self.tilt = self.MAX_ROTATION

        else:
            if self.tilt > -90:  # if the tilt is greater than -90 then keep on reducing it till it reaches -90 to show
                self.tilt -= self.ROTATION_VEL  # the arc like falling

    def draw(self, win):
        self.img_number += 1

        # below work is done to show the flapping of the bird
        # animation time is that for how much time bird should be in one image state
        if self.img_number < self.ANIMATION_TIME:
            self.img = self.IMGS[0]
        elif self.img_number < self.ANIMATION_TIME * 2:
            self.img = self.IMGS[1]
        elif self.img_number < self.ANIMATION_TIME * 3:
            self.img = self.IMGS[2]
        elif self.img_number < self.ANIMATION_TIME * 4:
            self.img = self.IMGS[1]
        elif self.img_number < self.ANIMATION_TIME * 4 + 1:
            self.img = self.IMGS[0]
            self.img_number = 0

        if self.tilt < -80:  # when the bird is nose diving it should not flap its wings
            self.img = self.IMGS[1]
            self.img_number = self.ANIMATION_TIME * 2  # reset the image number so that next image should be IMG[2]

        rotated_image = pygame.transform.rotate(self.img, self.tilt)  # just rotating the image around its center
        new_rect = rotated_image.get_rect(center=self.img.get_rect(topleft=(self.x, self.y)).center)
        win.blit(rotated_image, new_rect)

    def get_mask(self):  # getting the mask of the bird means the contour of bird to check its collision with any pipe
        return pygame.mask.from_surface(self.img)

class Pipe:
    GAP = 200
    VEL = 5

    def __init__(self, x):
        self.x = x
        self.height = 0  # for random purpose
        self.top = 0  # y coordinates of top pipe
        self.bottom = 0  # y coordinates of bottom pipe
        self.TOP_PIPE = pygame.transform.flip(PIPE_IMG, False, True)
        self.BOTTOM_PIPE = PIPE_IMG
        self.passed = False
        self.set_height()

    def set_height(self):  # randomly setting the heights of both pipes
        self.height = random.randrange(50, 450)
        self.bottom = self.height + self.GAP
        self.top = self.height - self.TOP_PIPE.get_height()

    def move(self):
        self.x -= self.VEL

    def draw(self, win):
        win.blit(self.TOP_PIPE, (self.x, self.top))
        win.blit(self.BOTTOM_PIPE, (self.x, self.bottom))

    def collide(self, bird):  # for checking collision of the bird with the pipes
        bird_mask = bird.get_mask()
        top_pipe_mask = pygame.mask.from_surface(self.TOP_PIPE)
        bottom_pipe_mask = pygame.mask.from_surface(self.BOTTOM_PIPE)

        top_offset = (self.x - bird.x, self.top - round(bird.y))
        bottom_offset = (self.x - bird.x, self.bottom - round(bird.y))

        top_overlap = bird_mask.overlap(top_pipe_mask, top_offset)
        bottom_overlap = bird_mask.overlap(bottom_pipe_mask, bottom_offset)

        if top_overlap or bottom_overlap:
            return True
        return False

# BASE Class for showing base
class Base:
    VEL = 5
    IMG = BASE_IMG
    WIDTH = BASE_IMG.get_width()

    def __init__(self,
                 y):  # base will be shown moving by taking two images of the same base and putting it one after other
        self.y = y
        self.x1 = 0  # here x1 and x2 are the 2 images where x1 comes first and then x2
        self.x2 = self.WIDTH

    def move(self):
        self.x1 -= self.VEL
        self.x2 -= self.VEL

        if self.x1 < -self.WIDTH:
            self.x1 = self.x2 + self.WIDTH
        if self.x2 < -(self.WIDTH):
            self.x2 = self.x1 + self.WIDTH

    def draw(self, win):
        win.blit(self.IMG, (self.x1, self.y))
        win.blit(self.IMG, (self.x2, self.y))

# Our main drawing function
def draw_window(win, birds, pipes, base, score, GEN, pipe_ind):
    global DRAW_LINES
    win.blit(BG_IMG, (0, 0))  # drawing the background
    for pipe in pipes:  # drawing the pipe or pipes as there can be more than one pipes also in one window
        pipe.draw(win)
    base.draw(win)  # drawing the base

    for bird in birds:
        # draw lines from bird to pipe
        if DRAW_LINES:
            try:
                pygame.draw.line(win, (255, 0, 0),
                                 (bird.x + bird.img.get_width() / 2, bird.y + bird.img.get_height() / 2),
                                 (pipes[pipe_ind].x + pipes[pipe_ind].TOP_PIPE.get_width() / 2, pipes[pipe_ind].height),
                                 5)
                pygame.draw.line(win, (255, 0, 0),
                                 (bird.x + bird.img.get_width() / 2, bird.y + bird.img.get_height() / 2), (
                                     pipes[pipe_ind].x + pipes[pipe_ind].BOTTOM_PIPE.get_width() / 2,
                                     pipes[pipe_ind].bottom), 5)
            except:
                pass

        bird.draw(win)

    text = STAT_FONT.render('Score : ' + str(score), 1, (255, 255, 255))  # printing the score on screen
    win.blit(text, (WIN_WIDTH - 10 - text.get_width(), 10))

    text = STAT_FONT.render('Gen : ' + str(GEN), 1, (255, 255, 255))  # printing the generation on screen
    win.blit(text, (10, 10))

    text = STAT_FONT.render('Alive : ' + str(len(birds)), 1, (255, 255, 255))  # printing the alive on screen
    win.blit(text, (10, 50))

    pygame.display.update()

def main(genomes, config):
    global GEN
    GEN += 1
    birds = []
    ge = []
    neural_networks = []

    # everytime new generation comes make new birds and neural networks
    for _, g in genomes:
        net = neat.nn.FeedForwardNetwork.create(g, config)
        neural_networks.append(net)
        birds.append(Bird(230, 350))
        g.fitness = 0
        ge.append(g)

    pipes = [Pipe(500)]  # list of pipe objects
    base_object = Base(630)
    win = pygame.display.set_mode((WIN_WIDTH, WIN_HEIGHT))
    clock = pygame.time.Clock()
    run = True
    score = 0

    # OUR main running loop

    while run:
        clock.tick(30)  # fps
        for event in pygame.event.get():
            if event.type == pygame.QUIT:  # if the user click on the red cross button then quit the game
                run = False
                pygame.quit()
                quit()

        pipe_ind = 0

        # this part is done to check in the case when 2 pipes appear on the screen that which is the pipe we are evaluating on
        if len(birds) > 0:
            if len(pipes) > 1 and birds[0].x > pipes[0].x + pipes[0].TOP_PIPE.get_width():
                pipe_ind = 1

        else:  # if all the birds are dead then exit the loop
            break

        for x, bird in enumerate(birds):  # traversing every bird
            bird.move()
            ge[x].fitness += 0.1  # incrementing little fitness to keep them  moving
            # this is the output list which the nn is giving for all the birds whether to jump or not
            output = neural_networks[x].activate(
                (bird.y, abs(bird.y - pipes[pipe_ind].height), abs(bird.y - pipes[pipe_ind].bottom)))
            if output[0] > 0.5:
                bird.jump()

        for pipe in pipes:
            for x, bird in enumerate(birds):
                # checking if the bird has hit the ground or if the pipe and bird collide or if the bird has touched te top boundary
                if pipe.collide(bird) or (bird.y + bird.img.get_height() >= 630 or bird.y < 0):
                    ge[x].fitness -= 1  # remove all things of that bird from that bird's position
                    birds.pop(x)
                    ge.pop(x)
                    neural_networks.pop(x)

                if not pipe.passed and bird.x > pipe.x:  # if the passed is not set to true and bird has passed the pipe then set it to true
                    pipe.passed = True
                    for g in ge:
                        g.fitness += 5  # adding fitness to birds which passed
                    score += 1
                    pipes.append(Pipe(500))  # add another pipe

            if pipe.x + pipe.TOP_PIPE.get_width() < 0:  # if pipe passed the screen remove it
                pipes.remove(pipe)

            pipe.move()

        base_object.move()
        draw_window(win, birds, pipes, base_object, score, GEN, pipe_ind)

def run(config_path):
    config = neat.config.Config(neat.DefaultGenome, neat.DefaultReproduction,
                                neat.DefaultSpeciesSet, neat.DefaultStagnation, config_path)
    population = neat.Population(config)
    population.add_reporter(neat.StdOutReporter(True))
    stats = neat.StatisticsReporter()
    population.add_reporter(stats)

    winner = population.run(main, 50)
    print('\nBest genome:\n{!s}'.format(winner))

if __name__ == '__main__':
    local_dir = os.path.dirname(__file__)
    config_path = os.path.join(local_dir, 'config-feedforward.txt')
    run(config_path)

# This was the code for Flappy Bird Game
```

*   第 1–4 行—导入 Flappy Bird 游戏所需的库。
*   第 8–11 行—一些常量。
*   第 16–21 行—导入鸟、管道、背景和底座的图像。
*   第 28–95 行—为 Flappy Bird 游戏创建鸟类。
*   第 98–137 行—为 Flappy Bird 游戏创建类管道。
*   第 141–163 行—为 Flappy Bird 游戏创建类库。
*   第 167–200 行——我们的主窗口，我们的游戏将在其中显示。
*   第 203–276 行——把所有的碎片放在一起，制作游戏。
*   第 279–288 行—这个函数将运行整个代码。这个函数还会告诉我们哪一代是最好的。
*   第 291–294 行——调用上面的 run 函数并传递配置文件的路径。

![](img/c21ad1cd1fe807098863867f4716b863.png)

bird in 1st position

![](img/f711120695645299bfba5ebeb97bec5f.png)

bird in 2nd position

![](img/c002b810298041f372d24f51de5b41ff.png)

bird in 3rd position

![](img/18635106e7cc1469bc0940af55957a4d.png)

pipe

![](img/c36bb33aba80dc9e30efd906765bd8ee.png)

base

![](img/5de50fc32e853ccf06793fc7d7ff91ee.png)

AI plays Flappy bird game

如果对 Flappy Bird 游戏有任何疑问，请通过电子邮件或 LinkedIn 联系我。你也可以在下面评论任何问题。

***探索更多机器学习、深度学习、计算机视觉、NLP、Flask 项目访问我的博客—*** [***机器学习项目***](https://machinelearningprojects.net/)

**如需进一步的代码解释和源代码，请访问此处**—[https://machine learning projects . net/ai-learning-to-play-flappy-bird-game/](https://machinelearningprojects.net/ai-learns-to-play-flappy-bird-game/)

这就是我写给这个博客的所有内容，感谢你的阅读，我希望你在阅读完这篇文章后，能有所收获，直到下次👋…

***阅读我之前的帖子:*** [***火灾和烟雾探测使用 CNN WITH KERAS***](https://machinelearningprojects.net/fire-and-smoke-detection/)

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)