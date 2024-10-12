This code implements a classic "Snake" game using the Pygame library. In this game, the player controls the snake to eat food, causing the snake to grow longer. If the snake collides with the walls or itself, the game is over. Let's go over the different parts of the code:

1. Pygame Initialization
pygame.init()

This line initializes Pygame and must be called before using any Pygame functions.

2. Defining Colors
white = (255, 255, 255)
yellow = (255, 255, 102)
black = (0, 0, 0)
red = (213, 50, 80)
green = (0, 255, 0)
blue = (50, 153, 213)

Various colors are defined using RGB format (Red, Green, Blue) and will be used throughout the game for drawing elements like the snake and background.

3. Screen Dimensions
dis_width = 800
dis_height = 600

The width and height of the game window are defined as 800 and 600 pixels, respectively.

4. Creating the Game Window
dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption('Snake Game')

This line creates a game window with the specified dimensions, and the window’s title is set to "Snake Game."

5. Time and Speed Settings
clock = pygame.time.Clock()
snake_block = 10
snake_speed = 15
pygame.time.Clock()

 is used to control the frame rate of the game. The snake_block variable defines the size of each snake segment, and snake_speed controls how fast the snake moves.

6. Fonts
font_style = pygame.font.SysFont("bahnschrift", 25)
score_font = pygame.font.SysFont("comicsansms", 35)

Two fonts are defined, one for displaying messages and one for displaying the score.

7. Drawing the Snake
def our_snake(snake_block, snake_list):
    for x in snake_list:
        pygame.draw.rect(dis, black, [x[0], x[1], snake_block, snake_block])

This function draws the snake on the screen. The snake_list contains the coordinates of the snake's body parts, and each part is drawn as a black rectangle.

8. Displaying Messages
def message(msg, color):
    mesg = font_style.render(msg, True, color)
    dis.blit(mesg, [dis_width / 6, dis_height / 3])

This function displays a message on the screen in a specific font and color. It's used to show messages like "You Lost!"

9. Main Game Loop
def gameLoop():

This function contains the main game loop and handles various game operations:

Initial Snake Position:


x1 = dis_width / 2
y1 = dis_height / 2

Snake and Food Initialization: At the start of the game, the snake is just one block long. The food is placed randomly on the screen:


foodx = round(random.randrange(0, dis_width - snake_block) / 10.0) * 10.0
foody = round(random.randrange(0, dis_height - snake_block) / 10.0) * 10.0

Main Game Loop: The game runs in a loop until the player loses. Inside the loop:

Event Handling: The player can use the arrow keys to control the snake's direction:


if event.key == pygame.K_LEFT:
Checking for Wall Collision: If the snake's head goes outside the screen, the game ends:


if x1 >= dis_width or x1 < 0 or y1 >= dis_height or y1 < 0:
    game_close = True

Drawing the Game Elements: The snake and the food are drawn on the screen:


our_snake(snake_block, snake_List)
pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])

Checking for Self-Collision: If the snake collides with itself, the game ends:


for x in snake_List[:-1]:
    if x == snake_Head:
        game_close = True

Checking for Eating Food: If the snake's head reaches the food, the snake grows longer and the food is repositioned randomly:

if x1 == foodx and y1 == foody:
    Length_of_snake += 1

    
10. Game Over
When the player loses, the message "You Lost" is displayed, and the player can choose to restart the game or quit.


این کد یک بازی کلاسیک "مار" را با استفاده از کتابخانه‌ی Pygame پیاده‌سازی می‌کند. در این بازی، بازیکن باید مار را هدایت کند تا غذا بخورد و با این کار طول مار افزایش پیدا کند. در صورت برخورد با دیوار یا برخورد مار با خودش، بازی تمام می‌شود. حالا قسمت‌های مختلف کد را بررسی می‌کنیم:

1. ابتدا‌سازی Pygame
pygame.init()
این خط، Pygame را برای استفاده در برنامه‌ی شما آماده می‌کند و باید قبل از استفاده از هر کدام از توابع آن فراخوانی شود.

2. تعریف رنگ‌ها
white = (255, 255, 255)
yellow = (255, 255, 102)
black = (0, 0, 0)
red = (213, 50, 80)
green = (0, 255, 0)
blue = (50, 153, 213)
رنگ‌های مختلفی برای نمایش عناصر بازی تعریف می‌شوند. این رنگ‌ها در فرمت RGB (مقادیر قرمز، سبز، آبی) تعریف شده‌اند.

3. ابعاد صفحه نمایش
dis_width = 800
dis_height = 600
در این بخش، عرض و ارتفاع پنجره بازی به ترتیب 800 و 600 پیکسل تعریف شده است.

4. ایجاد صفحه نمایش
dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption('Snake Game')
یک پنجره با اندازه مشخص (800x600) ایجاد می‌شود و عنوان پنجره "Snake Game" تنظیم می‌گردد.

5. تنظیمات زمان و سرعت
clock = pygame.time.Clock()
snake_block = 10
snake_speed = 15
اینجا از pygame.time.Clock() برای کنترل فریم‌های بازی استفاده می‌شود. snake_block اندازه هر بلوک مار را تعیین می‌کند و snake_speed سرعت حرکت مار در هر ثانیه است.

6. فونت‌ها
font_style = pygame.font.SysFont("bahnschrift", 25)
score_font = pygame.font.SysFont("comicsansms", 35)
دو فونت برای نمایش متن‌های مختلف در بازی تعریف شده‌اند. فونت اول برای پیام‌ها و فونت دوم برای نمایش امتیاز استفاده می‌شود.

7. تابع ترسیم مار
def our_snake(snake_block, snake_list):
    for x in snake_list:
        pygame.draw.rect(dis, black, [x[0], x[1], snake_block, snake_block])
این تابع برای رسم مار بر روی صفحه استفاده می‌شود. snake_list شامل مختصات بخش‌های مختلف مار است و در هر حلقه یک بلوک به رنگ سیاه رسم می‌شود.

8. تابع نمایش پیام
def message(msg, color):
    mesg = font_style.render(msg, True, color)
    dis.blit(mesg, [dis_width / 6, dis_height / 3])
این تابع یک پیام را با فونت و رنگ مشخص در صفحه نمایش نشان می‌دهد. از آن برای نمایش پیام‌هایی مانند "شما باختید" استفاده می‌شود.

9. تابع اصلی بازی

def gameLoop():
این تابع حلقه اصلی بازی را پیاده‌سازی می‌کند و بخش‌های مختلف بازی در آن مدیریت می‌شود:

موقعیت اولیه مار:


x1 = dis_width / 2
y1 = dis_height / 2
ایجاد لیست مار و غذا: در ابتدای بازی، مار فقط یک بلوک است. موقعیت غذا به صورت تصادفی در صفحه قرار داده می‌شود:


foodx = round(random.randrange(0, dis_width - snake_block) / 10.0) * 10.0
foody = round(random.randrange(0, dis_height - snake_block) / 10.0) * 10.0
حلقه اصلی بازی: بازی در یک حلقه اجرا می‌شود و تا زمانی که بازیکن بازنده نشده باشد، بازی ادامه می‌یابد. در این حلقه:

بررسی وقایع: بازیکن می‌تواند با استفاده از کلیدهای جهت‌نما مار را حرکت دهد:


if event.key == pygame.K_LEFT:
بررسی برخورد با دیوار: اگر موقعیت سر مار از صفحه خارج شود، بازی تمام می‌شود:


if x1 >= dis_width or x1 < 0 or y1 >= dis_height or y1 < 0:
    game_close = True
رسم عناصر بازی: مار و غذا روی صفحه رسم می‌شوند:


our_snake(snake_block, snake_List)
pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
بررسی برخورد مار با خودش: اگر مار به خودش برخورد کند، بازی تمام می‌شود:


for x in snake_List[:-1]:
    if x == snake_Head:
        game_close = True
بررسی خوردن غذا: اگر سر مار به غذا برسد، طول مار افزایش پیدا می‌کند و غذا در جای جدیدی قرار داده می‌شود:


if x1 == foodx and y1 == foody:
    Length_of_snake += 1
10. پایان بازی
وقتی بازیکن می‌بازد، پیام "You Lost" نمایش داده می‌شود و بازیکن می‌تواند بازی را مجدد شروع کند یا آن را ترک کند.
