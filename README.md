# MonkeyAndBananasGame
Try to catch as many bananas as you can in 15 seconds!

    #imports
    import simplegui, random, math

    #initialize variables
    canvas_width = 700											#keeps track of canvas width
    canvas_height = 400											#keeps track of canvas height

    monkey_vel = [0,0]											#keeps track of the velocity of the monkey
    monkey = simplegui.load_image("https://docs.google.com/uc?export=download&id=1bKiEfQCALHiHkMBt6BW--VpciOI0Vx3M")
    monkey_height = 2000										#keeps track of the monkey height
    monkey_width= 2000					 						#keeps track of the monkey width
    monkey_center = [420, 300]									#keeps track of the center of the monkey

    banana_image = simplegui.load_image("https://docs.google.com/uc?export=download&id=1Ks-Sm1vk2tiUnHQ3zRv-HXyaK7XKE1Y8")
    banana_width = 2084											#keeps track of the width of the banana
    banana_height = 2084											#keeps track of the height of the banana
    #bananas 1 to 8
    banana_center_list1 = [[0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30]]
    banana_vel_list1 = [0, 0, 0, 0, 0, 0, 0, 0]					#keeps track of the vel for bananas 1 to 8
    #bananas 9 to 16
    banana_center_list2 = [[0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30]]
    banana_vel_list2 = [0, 0, 0, 0, 0, 0, 0, 0]					#keeps track of the vel for bananas 9 to 16

    time = 0													#keeps track of the time	
    time_left = 15												#keeps track of the time left
    score = 0													#keeps track of the score

    #helper function
    def check_banana_eaten():
        global banana_center_list1, banana_center_list2, score
        for i in range (0, 7):
            if (monkey_center[1] - 50 <= banana_center_list1[i][1] <= monkey_center[1] + 50) and (monkey_center[0] - 50 <= banana_center_list1[i][0] <= monkey_center[0] + 50):
                score = score + 1
                print("---------------------------")
                print("SCORE: ", score)
                banana_center_list1[i][1] = -30
                banana_vel_list1[i] = 0
            if (monkey_center[1] - 50 <= banana_center_list2[i][1] <= monkey_center[1] + 50) and (monkey_center[0] - 50 <= banana_center_list2[i][0] <= monkey_center[0] + 50):
                score = score + 1
                print("---------------------------")
                print("SCORE: ", score)
                banana_center_list2[i][1] = -30
                banana_vel_list2[i] = 0
            i = i + 1

    def update_monkey():										#function that updates the center of the monkey
        global monkey_center
        monkey_center[0] = monkey_center[0] + monkey_vel[0]		#moves the monkey left and right
        monkey_center[1] = monkey_center[1] + monkey_vel[1]		#moves the monkey up and down
        keep_monkey_on_canvas()									#calls the function that keeps the monkey on the canvas

    def keep_monkey_on_canvas():								#function that keeps the monkey on the canvas
        global monkey_vel
        #if the monkey hits the left or right boarders
        if monkey_center[0] <= 0:								#if the monkey touches the left border then it stops
            monkey_vel[0] = 0
        if monkey_center[0] >= canvas_width:					#if the monkey touches the right border then it stops
            monkey_vel[0] = 0

    def spawn_bananas(banana_num):								#function that spawns bananas
        global banana_vel_list1,banana_center_list1, banana_vel_list2, banana_center_list2
        print("banana_num: ", banana_num)
        #bananas 1 through 8 fall every second
        if banana_num == 1 or banana_num == 9:
            banana_center_list1[0][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list1[0] = random.randrange(1, 5)
            print("Banana 1: ", banana_center_list1[0][0])
        elif banana_num == 2 or banana_num == 10:
            banana_center_list1[1][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list1[1] = random.randrange(1, 5)
            print("Banana 2: ",banana_center_list1[1][0])
        elif banana_num == 3 or banana_num == 11:
            banana_center_list1[2][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list1[2] = random.randrange(1, 5)
            print("Banana 3: ",banana_center_list1[2][0])
        elif banana_num == 4 or banana_num == 12:
            banana_center_list1[3][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list1[3] = random.randrange(1, 5)
            print("Banana 4: ",banana_center_list1[3][0])
        elif banana_num == 5 or banana_num == 13:
            banana_center_list1[4][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list1[4] = random.randrange(1, 5)
            print("Banana 5", banana_center_list1[4][0])
        elif banana_num == 6 or banana_num == 14:
            banana_center_list1[5][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list1[5] = random.randrange(1, 5)
            print("Banana 6", banana_center_list1[5][0])
        elif banana_num == 7 or banana_num == 15:
            banana_center_list1[6][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list1[6] = random.randrange(1, 5)
            print("Banana 7", banana_center_list1[6][0])
        elif banana_num == 8 or banana_num == 16:
            banana_center_list1[7][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list1[7] = random.randrange(1, 5)
            print("Banana 8", banana_center_list1[7][0])
        #bananas 9 through 16 fall at half seconds to create more bananas on screen    
        elif banana_num == 0.5 or banana_num == 8.5:
            banana_center_list2[0][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list2[0] = random.randrange(1, 5)
            print("Banana 9: ", banana_center_list2[0][0])
        elif banana_num == 1.5 or banana_num == 9.5:
            banana_center_list2[1][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list2[1] = random.randrange(1, 5)
            print("Banana 10: ",banana_center_list2[1][0])
        elif banana_num == 2.5 or banana_num == 10.5:
            banana_center_list2[2][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list2[2] = random.randrange(1, 5)
            print("Banana 11: ",banana_center_list2[2][0])
        elif banana_num == 3.5 or banana_num == 11.5:
            banana_center_list2[3][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list2[3] = random.randrange(1, 5)
            print("Banana 12: ",banana_center_list2[3][0])
        elif banana_num == 4.5 or banana_num == 12.5:
            banana_center_list2[4][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list2[4] = random.randrange(1, 5)
            print("Banana 13", banana_center_list2[4][0])
        elif banana_num == 5.5 or banana_num == 13.5:
            banana_center_list2[5][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list2[5] = random.randrange(1, 5)
            print("Banana 14", banana_center_list2[5][0])
        elif banana_num == 6.5 or banana_num == 14.5:
            banana_center_list2[6][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list2[6] = random.randrange(1, 5)
            print("Banana 15", banana_center_list2[6][0])
        elif banana_num == 7.5 or banana_num == 15.5:
            banana_center_list2[7][0] = random.randrange(30, canvas_width - 200)
            banana_vel_list2[7] = random.randrange(1, 5)
            print("Banana 16", banana_center_list2[7][0])  

    def update_banana_position():								#function that updates the position of the Bananas
        global banana_center_list1, banana_center_list2
        #updates Bananas 1 to 8 position
        for i in range (0, 7):
            banana_center_list1[i][1] = banana_center_list1[i][1] + banana_vel_list1[i]
            i = i + 1
        #updates Bananas 9 to 16 position
        for i in range (0, 7):
            banana_center_list2[i][1] = banana_center_list2[i][1] + banana_vel_list2[i]
            i = i + 1 
        #puts the Bananas back above the top of the screen when they hit the ground
        for i in range (0, 7):
            if banana_center_list1[i][1] >= 320:
                banana_center_list1[i][1] = -30
                banana_vel_list1[i] = 0
            if banana_center_list2[i][1] >= 320:
                banana_center_list2[i][1] = -30
                banana_vel_list2[i] = 0
            i = i + 1

    #def handler functions
    def keydown(key):											#function that changes the monkey vel to move it
        global monkey_vel
        if key == simplegui.KEY_MAP['left'] and monkey_center[0] > 0: 				#sees if the left key is pressed
            monkey_vel[0] = -3
        elif key == simplegui.KEY_MAP['right'] and monkey_center[0] < canvas_width:	#sees if the right key is pressed
            monkey_vel[0] = 3

    def keyup(key):												#function that sets vel to zero if key is up
        global monkey_vel
        if key == simplegui.KEY_MAP['left']:					#sees if left key is up
            monkey_vel[0] = 0
        elif key == simplegui.KEY_MAP['right']:					#sees if right key is up
            monkey_vel[0] = 0

    def start_handler():										#when start button is pressed then this function is called
        global time
        timer.start()											#starts the timer
        time = time + 1

    def timer_handler():										#timer function
        global time, time_left
        time_left = 15 - time
        time_left = math.ceil(time_left)
        print("Time Left: ", time_left)
        spawn_bananas(time)										#spawns an Banana every half a second
        time = time + 0.5
        spawn_bananas(time)										#spawns an Banana every half a second
        time = time + 0.5
        if time == 15:											#the game is over after 15 seconds
            frame.set_draw_handler(game_over_handler)

    def draw_handler(canvas):
        update_monkey()
        update_banana_position()
        check_banana_eaten()
        #draws the monkey
        canvas.draw_image(monkey, (monkey_width/2, monkey_height/2), (monkey_width*3/4, monkey_height*3/4), (monkey_center[0], monkey_center[1]), (100, 80))
        #graws the green grass/ground
        canvas.draw_polygon([(0, canvas_height), (canvas_width, canvas_height), (canvas_width, 350), (0, 350)], 20, 'Green', 'Green')
        #draws Bananas 1 to 8
        for i in range(0,7):
            canvas.draw_image(banana_image,(banana_width/2, banana_height/2), (banana_width, banana_height), banana_center_list1[i],(60,60))
            i = i + 1
        #draws Bananas 9 to 16
        for i in range(0,7):
            canvas.draw_image(banana_image,(banana_width/2, banana_height/2), (banana_width, banana_height), banana_center_list2[i],(60,60))
            i = i + 1
        #tells the user how much time is left
        canvas.draw_text("TIME LEFT", (360, 32), 25, 'white')
        canvas.draw_text(str(time_left), (390, 96), 64, 'red')
        #tells the user their score
        canvas.draw_text("SCORE", (385, 130), 25, 'white')
        canvas.draw_text(str(score), (410, 180), 64, 'red')

    def game_over_handler(c):										#handler that controls the game over screen
        #stops the timer
        timer.stop()
        #tells the user the game is over and their score
        c.draw_text("GAME OVER",(80,100),64,"orange")
        c.draw_text(("SCORE: " + str(score)), (150, 200), 50, 'red')
        #draws the monkey
        c.draw_image(monkey, (monkey_width/2, monkey_height/2), (monkey_width*3/4, monkey_height*3/4), (monkey_center[0], monkey_center[1]), (100, 80))
        #graws the green grass/ground
        c.draw_polygon([(0, canvas_height), (canvas_width, canvas_height), (canvas_width, 350), (0, 350)], 20, 'Green', 'Green')

    def button_quit_handler():										#if the user hits quit game it ends it
        timer.stop()
        frame.stop()

    def restart_handler():											#if the user hits restart the game is reset
        global banana_vel_list1, banana_center_list1, banana_vel_list2, banana_center_list2
        global monkey_vel, monkey_center, time, time_left, score
        #stops the timer
        timer.stop()

        #resets all the varriables
        monkey_vel = [0,0]											#keeps track of the velocity of the monkey
        monkey_center = [420, 300]									#keeps track of the center of the monkey

        time = 0													#keeps track of the time
        time_left = 15												#keeps track of the time left
        score = 0													#keeps track of the score

        banana_center_list1 = [[0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30]]
        banana_vel_list1 = [0, 0, 0, 0, 0, 0, 0, 0]					#keeps track of the vel for bananas 1 to 8
        banana_center_list2 = [[0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30], [0, -30]]
        banana_vel_list2 = [0, 0, 0, 0, 0, 0, 0, 0]					#keeps track of vel for bananas 9 through 16

        #restarts the timer
        timer.start()											
        time = time + 1

        #resets the frame in case the user is in the game over screen
        frame.set_draw_handler(draw_handler)

    #set frame
    frame = simplegui.create_frame('Monkey and Bananas', 500, 400)
    frame.set_canvas_background("cyan")

    #set and create handlers
    frame.set_keydown_handler(keydown)
    frame.set_keyup_handler(keyup)

    timer = simplegui.create_timer(1000, timer_handler)
    frame.set_draw_handler(draw_handler)

    frame.add_button("START",start_handler,80)
    frame.add_button("RESTART", restart_handler, 80)
    frame.add_button("QUIT", button_quit_handler, 80)

    #start frame
    frame.start()
