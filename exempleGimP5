import random

from pygame.math import Vector2
import core

def setup():
    print("Setup START---------")
    core.fps = 120
    core.WINDOW_SIZE = [400, 400]
    core.memory("centreDuCercle",Vector2(200,200))
    core.memory("vitesseDuCercle", Vector2(0, 0))
    core.memory("accDuCercle", Vector2(0, 0))
    core.memory("rayon",10)

    core.memory("hautgauche",Vector2(random.randint(0,core.WINDOW_SIZE[0]),random.randint(0,core.WINDOW_SIZE[1])))
    core.memory("cote",10)
    print("Setup END-----------")

def getGravity(value=9):
    return value

def control():
    if core.getKeyPressList("r"):
        core.memory("centreDuCercle", Vector2(200, 0))
        core.memory("vitesseDuCercle", Vector2(0, 0))
        core.memory("accDuCercle", Vector2(0, 0))

    core.memory("accDuCercle", Vector2(0, 0))
    if core.getKeyPressList("d"):
        core.memory("accDuCercle", Vector2(core.memory("accDuCercle").x+1, core.memory("accDuCercle").y))
    if core.getKeyPressList("q"):
        core.memory("accDuCercle", Vector2(core.memory("accDuCercle").x - 1, core.memory("accDuCercle").y))
    if core.getKeyPressList("z"):
        core.memory("accDuCercle", Vector2(core.memory("accDuCercle").x , core.memory("accDuCercle").y-1))
    if core.getKeyPressList("s"):
        core.memory("accDuCercle", Vector2(core.memory("accDuCercle").x , core.memory("accDuCercle").y+1))




def update():
    core.memory("centreDuCercle", Vector2(core.memory("centreDuCercle").x, core.memory("centreDuCercle").y + getGravity(0)))
    core.memory("vitesseDuCercle", core.memory("vitesseDuCercle") + core.memory("accDuCercle"))
    core.memory("centreDuCercle",core.memory("centreDuCercle")+core.memory("vitesseDuCercle"))

def show():
    core.Draw.circle((255,255,255),core.memory("centreDuCercle"),core.memory("rayon"))
    core.Draw.rect((255,0,0),(core.memory("hautgauche").x,core.memory("hautgauche").y,core.memory("cote"),core.memory("cote")))

def edge():
    if core.memory("centreDuCercle").y < core.memory("rayon") :
        core.memory("centreDuCercle",Vector2(core.memory("centreDuCercle").x,core.memory("rayon")))
        if core.memory("vitesseDuCercle").y < 0:
            core.memory("vitesseDuCercle", Vector2(core.memory("vitesseDuCercle").x, 0))
            core.memory("accDuCercle", Vector2(core.memory("accDuCercle").x, 0))


    if core.memory("centreDuCercle").y > core.WINDOW_SIZE[1]-core.memory("rayon") :
        core.memory("centreDuCercle",Vector2(core.memory("centreDuCercle").x,core.WINDOW_SIZE[1]-core.memory("rayon")))
        if core.memory("vitesseDuCercle").y > 0:
            core.memory("vitesseDuCercle", Vector2(core.memory("vitesseDuCercle").x, 0))
            core.memory("accDuCercle", Vector2(core.memory("accDuCercle").x, 0))

def run():
    core.cleanScreen()
    control()
    edge()
    update()
    show()





core.main(setup, run)
