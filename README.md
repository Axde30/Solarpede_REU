# Solarpede_randomizer_tracker
this is for the 2022 REU program in UofL 
import pyautogui as pg
import mouseinfo
import random
import time
import subprocess
from tkinter import *
from tkinter import ttk
#from tracking_v4 import *
'''This code will randomize the commands given to the robot. you can randomize all the actuators at the same time, randomize specific actuators, or randomize groups of actuators with the right functions.'''

filepath_teraterm = (r"C:\Program Files (x86)\teraterm\ttermpro.exe")  # change to correct filepath for teraterm    Ex: r"C:\Program Files (x86)\teraterm\ttermpro.exe"
#filepath_teraterm = (r"C:\Windows\System32\notepad.exe") #FOR TESTING ONLY!! THIS IS MY FILEPATH FOR NOTEPAD TO SEE IF THE COMMANDS OUTPUT
pulse = "p100"  # change to desired pulse   Ex: p100
number_of_rounds = 1  # change to edit the number of rounds     Ex: 5

m_commands = ("m1", "m2", "m3", "m4", "m5", "m6", "m7", "m8")
possible_commands = ("00001",
                "00010",
                "00011",
                "00100",
                "00101",
                "00110",
                "00111",
                "01000",
                "01001",
                "01010",
                "01011",
                "01100",
                "01101",
                "01110",
                "01111",
                "10000",
                "10001",
                "10010",
                "10011",
                "10100",
                "10101",
                "10110",
                "10111",
                "11000",
                "11001",
                "11010",
                "11011",
                "11100",
                "11101",
                "11110",
                "11111",
                "00000")


def movement_randomizer():
    '''This will randomize all actuators with all commands'''
    pg.write(random.choice(m_commands))
    commands = possible_commands  # fill in the remaining commands and randomize the picking
    pg.write(random.choice(commands))
    pg.press('enter')


def actuator_1():
    '''function to control and randomize individual actuator 1'''
    pg.write(m_commands[0])
    commands = possible_commands  # fill in the remaining commands and randomize the picking

    a = random.choice(commands)
    pg.write(a)
    pg.press('enter')
    return m_commands[0] + a




def actuator_2():
    '''function to control and randomize individual actuator 2'''
    pg.write(m_commands[1])
    commands = possible_commands  # fill in the remaining commands and randomize the picking
    a = random.choice(commands)
    pg.write(a)
    pg.press('enter')
    return m_commands[1] + a


def actuator_3():
    '''function to control and randomize individual actuator 3'''
    pg.write(m_commands[2])
    commands = possible_commands  # fill in the remaining commands and randomize the picking
    a = random.choice(commands)
    pg.write(a)
    pg.press('enter')
    return m_commands[2] + a


def actuator_4():
    '''function to control and randomize individual actuator 4'''
    pg.write(m_commands[3])
    commands = possible_commands  # fill in the remaining commands and randomize the picking
    a = random.choice(commands)
    pg.write(a)
    pg.press('enter')
    return m_commands[3] + a


def actuator_5():
    '''function to control and randomize individual actuator 5'''
    pg.write(m_commands[4])
    commands = possible_commands  # fill in the remaining commands and randomize the picking
    a = random.choice(commands)
    pg.write(a)
    pg.press('enter')
    return m_commands[4] + a


def actuator_6():
    '''function to control and randomize individual actuator 6'''
    pg.write(m_commands[5])
    commands = possible_commands  # fill in the remaining commands and randomize the picking
    a = random.choice(commands)
    pg.write(a)
    pg.press('enter')
    return m_commands[5] + a

def actuator_7():
    '''function to control and randomize individual actuator 7'''
    pg.write(m_commands[6])
    commands = possible_commands  # fill in the remaining commands and randomize the picking
    a = random.choice(commands)
    pg.write(a)
    pg.press('enter')
    return m_commands[6] + a


def actuator_8():
    '''function to control and randomize individual actuator 8'''
    pg.write(m_commands[7])
    commands = possible_commands  # fill in the remaining commands and randomize the picking
    a = random.choice(commands)
    pg.write(a)
    pg.press('enter')
    return m_commands[7] + a


def actuator_group1():
    '''function to randomize one of the 4 legs of the robot'''
    actuator_1()
    actuator_2()


def actuator_group2():
    '''function to randomize one of the 4 legs of the robot'''
    actuator_3()
    actuator_4()


def actuator_group3():
    '''function to randomize one of the 4 legs of the robot'''
    actuator_5()
    actuator_6()


def actuator_group4():
    '''function to randomize one of the 4 legs of the robot'''
    actuator_7()
    actuator_8()


def display():
    '''Displays a chart of active commands and pulse'''
    pg.write("d")
    pg.press('enter')


def start():
    '''commence operation'''
    pg.write("w")
    pg.press('enter')


def stop():
    '''stop operation'''
    pg.write("s")
    pg.press('enter')


def initialize():
    '''starting program commands:
    resets all the defaults from miniterm.'''
    pg.write(pulse)
    pg.press('enter')
    stop()
    pg.write("m100000")
    pg.press('enter')
    display()


def tera_main():
    '''Main traning program:
    EDIT: use the functions to create your custom traning program '''
    i = 1
    teraterm = subprocess.Popen(filepath_teraterm)
    time.sleep(5)
    initialize()
    while i <= number_of_rounds:
        time.sleep(1)
        movement_randomizer()
        time.sleep(1)
        display()
        time.sleep(1)
        start()
        time.sleep(3)
        # display()
        # mouseinfo.MouseInfoWindow()
        # time.sleep(1)
        stop()
        print(i)

        i += 1
    teraterm.terminate()


def tera_actuator_groups():
    '''Main traning program:
    EDIT: use the functions to create your custom traning program '''
    i = 1
    #recording1 = record_session()
    print("!!!DO NOT TOUCH!!!")
    teraterm = subprocess.Popen(filepath_teraterm)
    time.sleep(3)

    initialize()

    while i <= number_of_rounds:
        time.sleep(1)
        actuator_group1()
        time.sleep(1)
        actuator_group2()
        time.sleep(1)
        actuator_group3()
        time.sleep(1)
        actuator_group4()
        time.sleep(1)
        display()
        time.sleep(1)
        start()
        time.sleep(3)
        # display()
        # mouseinfo.MouseInfoWindow()
        # time.sleep(1)
        stop()
        print(i)

        i += 1
    #get_coordinates(recording1)
    start()
    teraterm.terminate()
    #plot_data()


def demo():
    i = 1
    teraterm = subprocess.Popen(filepath_teraterm)
    time.sleep(1)
    initialize()
    while i <= number_of_rounds:
        movement_randomizer()
        time.sleep(1)
        display()
        time.sleep(10)
        start()
        print(i)
        stop()
        i += 1
    start()
    # teraterm.terminate()


class UserInput(object):
    '''this class is to create Gui interfaces to change the settings of the program'''

    def ButtonCommand(self, text, command):
        btn = ttk.Button(text=text, command=command)
        btn.pack()

    def get_input(self):
        Label.config(text="" + self.text.get(1.0, "end-1c"))
        Label.pack()

    def window_Settings(self, title, geometry, width, height):
        # Create an instance of tkinter frame
        self.window = Tk()

        self.text.insert(END, "")
        self.text.pack()
        self.label = Label(self.window, text="", font=('Calibri 15'))
        self.label.pack()
        # self.window.mainloop()

    # Create a Label widget
    @staticmethod
    def label():
        Label.pack()

    def close_loop(self):
        self.window.mainloop()

    # def testClass(self):p100

    #   ButtonCommand("Print", self.m6
    #   get_input())
#tera_actuator_groups()#randomize legs in groups
#tera_main()#Randomize all the legs at the same time
#UserInput()# test this to see if button works

#tera_actuator_groups()
#print(actuator_6())



#print(actuator_group3())
'''
gui = UserInput()


gui.window_Settings("Tera Term Randomizer", "700x350+800+450", 80, 15)
gui.ButtonCommand("print", tera_main())
gui.close_loop()

'''
