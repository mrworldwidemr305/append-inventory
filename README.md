# append-inventory
#ONCE DONE NEED TO ADD ALL THE CODES WORKED ON THIS TOGETHER SUCH AS dc 11-29, AND 11-30 
print("You wake up on the floor in a room, you look around, wondering where you are.")
print("All of a sudden you hear a voice from the speaker that is connected to your room.")
print("It says: Welcome you have been selected to participate in this experient, you have 96 hours to escape, if you do not escape in time the helicopter that is here to take you back home will leave.")
print("Good luck")

import random
#start of game loop------------------------------------------------------------------------------------------------------------------------
inventory = []#WILL ADD THINGS TO THIS LIST ONCE THE PLAYER FINDS THE ITEMS IN THE GAME
doExit = False #runs game loop
room = 1
choice = 'a'
def FloorFall():
    num = random.randrange(0, 100)
    if num < 65 :
        print("The floor opens you are falling down into a tank full of sharks, You have DIED!!!!")
        return True
    else:
        print("the floor feels soggy!!!")
        return False
    print("your inventory:", end = "")
    print(inventory)
while doExit == False:#WILL HAVE TO REMOVE THIS ONCE YOU ADD THE TIMER SINCE THAT HAS GAME LOOP AS WELL
#room1-------------------------------------------------------------------------------------------------------------------------------------

    if room ==1: #NEED TO ADD THE SWORD TO THERE INVENTORY
        print("you are in room 1, you can go (e)ast")
        print("In this room there is nothing in your surroundings but a wooden sword right next to your feet")
        choice = input()
        inventory.append("woodend sword")#I want them to have the option of getting the sword back for if they break it in room 4
        print("You chose to take the sword with you, as you exit and move to the next room")
        if choice == 'e' or choice == 'east':
            room = 2
        else:
            print("Not an option")
        print(inventory)
#room2-------------------------------------------------------------------------------------------------------------------------------------
    if room ==2:#YOU CANT GO TO ROOM 7 THROUGH HERE SINCE IT IS LOCKED #NEED TO ADD THAT THEY GOT A KEY FOR INVENTORY
        #SHOULD I ADD AN OPTION OF getting keys for shortcuts to go to room 7?
        print("you are in room 2, you can go (w)est or (s)outh or (e)ast, There is a bookshelf full of cobwebs in the corner. Would you like to look at it? (y)es")
        choice = input()
        if choice == 'yes' or choice == "y":
            print("you found a key!!!")#MAKE IT SO THAT THEY CAN ONLY FIND THE KEY ONCE AND CAN NOT HAVE MULTIPLE OF THE KEYS
            inventory.append("key")#HAVE TO MAKE IT SO ONLKY ONE KEY COMES OUT
        if choice == 'west' or choice == 'w':
            room = 1
        elif choice == 'south' or choice == 's':
            room = 3
        elif choice == 'east' or choice == 'e':
            print("The door to room 7 is locked try going west or south!")
        print(inventory)
#room3--------------------------------------------------------------------------------------------------------------------------------------
    if room ==3:#SAME AS ROOM 2 #ALSO NEED TO ADD INVENTORY SAYING THEY GOT POTION
        print("you are in room 3 in this room there are vials with liquids in them, you can go (n)orth, (s)outh, or (e)ast")
        choice = input()
        print("you take one of those vials and they so happen to be a health potion")#THE VIAL OF HEALTH POTION IS ADDED EVERY TIME THEY COME BACK TO THIS ROOM
        inventory.append("health potion")
        if choice == 'north' or choice == 'n':
            room = 2
        elif choice == 'south' or choice == 's':
            room = 4
        elif choice == 'east' or choice == 'e':
            print("Can not go to room 6 door is locked, try going to room 4")
        else:
            print("Not an option")
        print(inventory)
#room4--------------------------------------------------------------------------------------------------------------------------------------
    if room ==4:#NEED TO REMOVE SWORD IF THEY USE SWORD TO OPEN CHEST 
        print("you are in room 4, you can go north(n) or east(e), or look at the brown wooden chest to the right of you. would you like to use the (s)word or (k)ey for the chest (y)es or (n)o")
        choice = input()
        if choice == 'yes' or choice == 'y':
             print("use (w)ooden sword or (k)ey")
        choice = input()
        if choice == 'woodensword' or choice == 'w' or choice == 'W':
            print("You broke your sword, you should try the key")
            hasWoodenSword = False
            for i in range(len(inventory)):
                if inventory[i] == 'wooden sword':
                    hasWoodenSword = True
                if hasWoodenSword== True:
                    inventory[i] = ""#ERASE SWORD?
                    print(inventory)
        elif choice == 'key' or choice == 'k' or choice == 'K':
            hasWoodensword=False
            print("Go back to the rooms before and look for a key")
            hasKey = False
            for i in range(len(inventory)):#HAM REPEATS TWICE AND IT REPLACES HELATH POTION
                if inventory[i] == 'key':
                    hasKey = True
                if hasKey== True:
                    inventory.append("HAM!!!")
                    print("You opened the chest in the corner with the key, in chest there is ham")#repeats 
                    inventory[i] = "" #erase the key
                    print(inventory)
        if choice == 'north' or choice == 'n':
            room = 3
        elif choice == 'east' or choice == 'e':
            room = 5
        print(inventory)    
#Room 5-------------------------------------------------------------------------------------------------------------------------------------  
    if room ==5:
        print("you are in room 5,you can go (n)orth or (w)est ")
        choice = input()
        if FloorFall() == True:
            doExit = True#THE PROBABILITY OF THE PERSON DYING IS 65% AND THEN THE PLAYER MUST RESTART
            break
        if choice == 'north' or choice == 'n':
            room = 6
        elif choice == 'west' or choice == 'w':
            room = 4
        else:
            print("Not an option")
        print(inventory)
#Room 6------------------------------------------------------------------------------------------------------------------------------------
    if room ==6:
        print("you are in room 6, you can go north(n) or west(w)")
        choice = input()
        if choice == 'north' or choice == 'n':
            room = 7
        elif choice == 'west' or choice == 'w':
            room = 3
        else:
            print("Not an option")
        print(inventory)
#Room 7-------------------------------------------------------------------------------------------------------------------------------------          
    if room ==7:
        print("you are in room 7, you can go west(w), south(s) or (e)ast")
        choice = input()
        if choice == 'west' or choice == 'w':
            room = 2
        elif choice == 'south' or choice == 's':
            room = 6
        elif choice == 'east' or choice == 'e':
            room = 8
        else:
            print("Not an option")
        print(inventory)
#Room 8-------------------------------------------------------------------------------------------------------------------------------------          
    if room ==8:
        print("you are in room 8, you can go west(w) or (s)outh", "You seem to be hungry do you wish to eat your ham?, (y)es or (n)o")
        choice = input()
        if choice == 'yes' or choice == 'y':#NEED TO FIX TO REMOVE HAM IF IT WAS EATEN
            if inventory[4]=='ham':
                print("you have eaten your ham")
                inventoru[4]= "empty"
        elif choice == 'no' or choice == 'n':
            print("You chose to not eat your ham :(")
        choice = input()
        if choice == 'west' or choice == 'w':
            room = 7
        elif choice == 'south' or choice == 's':
            room = 9
        else:
            print("Not an option")
        print(inventory)
#Room 9------------------------------------------------------------------------------------------------------------------------------------           
    if room ==9:#THIS IS LIKE THAT LAST LEVEL THAT THE PERSON MUST COMPLETE TO MAKE IT OUT
        print("you are in room 9, In this room you see a tiger guarding the entrance to room 10, you can go west(w), north(n), or (e)ast, would youl like to give it your ham?")
        choice = input()
        if choice == 'yes' or choice == 'y':
            print("Quick leave, the tiger is distracted")
        elif choice == 'no' or choice == 'n':
            print("You try to fight off the tiger but it is to fast for you and choses to eat you, you have died!!!:(")
        #ADD SOMETHING SO THE PERSON DIES IF THEY CHOSE NO
        choice = input()
        if choice == 'west' or choice == 'w':
            room = 6
        elif choice == 'north' or choice == 'n':
            room = 8
        elif choice == 'east' or choice == 'e':
            room = 10
        else:
            print("Not an option")
        print(inventory)
#Room 10------------------------------------------------------------------------------------------------------------------------------------
    if room ==10:#NEED TO ADD SOMETHING SO THAT IF THEY DO NOT MAKE IT IN TIME THE HELECOPTER LEAVES WITH OUT THEM AND THEY ARE STRANDED THERE OR IF THEY DO MAKE IT THEY LEAVE WITH THE HELICOPTER
            print("you are in room 10 the last room that you need to escape from, you can go (s)outh or (e)ast")
            choice = input()
            if choice == 'south' or choice == 's':
                room = 9
            elif choice == 'east' or choice == 'e':
                room = 11
                print("CONGRATULATIONS YOU HAVE ESCAPED THE BUILDING. As you exit the building your eyes adjust to the bright, as you look at your surroundings you see that you are in the middle of nowhere")
            else:
                print("Not an option")
            print(inventory)
#end of game loop --------------------------------------------------------------------------------------------------------------------------

