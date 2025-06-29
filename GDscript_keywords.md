```gdscript
# 📘 GDScript Keywords
# Each keyword has:
# Purpose: What it's used for
# Usage: How to use it correctly
# Formula: A simple example in real code

# === VARIABLES ===

# var
# Purpose: Define a variable that can change
# Usage: Used for anything that changes during gameplay
# Formula:
var hp = 100

# const
# Purpose: Define a value that never changes
# Usage: Use for fixed values like gravity, limits, etc.
# Formula:
const MAX_SPEED = 400

# export
# Purpose: Let you adjust variables in the editor
# Usage: Use for speed, health, jump force, etc.
# Formula:
export var speed := 200

# onready
# Purpose: Access a node after the scene is ready
# Usage: Combine with $NodePath to get node references
# Formula:
onready var cam = $Camera2D

# class_name
# Purpose: Give your script a global name
# Usage: Let you use this script as Player.new()
# Formula:
class_name Player

# extends
# Purpose: Inherit functionality from another class
# Usage: Always write at the top of the script
# Formula:
extends CharacterBody2D

# === FUNCTIONS ===

# func
# Purpose: Define your own custom behavior
# Usage: Write reusable code blocks for logic
# Formula:
func jump():
    velocity.y = -300

# return
# Purpose: Exit a function early
# Usage: Use when a condition is met and no need to continue
# Formula:
func check():
    if hp <= 0:
        return

# === FLOW CONTROL ===

# if / elif / else
# Purpose: Make decisions in code
# Usage: Use when checking multiple conditions
# Formula:
if hp <= 0:
    die()
elif hp < 50:
    warn()
else:
    idle()

# match
# Purpose: Cleaner switch-style condition
# Usage: Use when checking many equal values
# Formula:
match direction:
    "left": move_left()
    "right": move_right()

# for
# Purpose: Loop through ranges or arrays
# Usage: Do something many times or per item
# Formula:
for i in range(5):
    print(i)

# while
# Purpose: Repeat while condition is true
# Usage: Use for state loops
# Formula:
while hp > 0:
    regen()

# === INPUT ===

# Input.is_action_pressed()
# Purpose: Check if key is being held
# Usage: Use in _process or _physics_process
# Formula:
if Input.is_action_pressed("ui_right"):
    velocity.x += speed

# Input.is_action_just_pressed()
# Purpose: Detect first key press
# Usage: Trigger jump, attack, etc.
# Formula:
if Input.is_action_just_pressed("jump"):
    jump()

# Input.get_action_strength()
# Purpose: Get analog input (0.0 to 1.0)
# Usage: For controller triggers or combined inputs
# Formula:
var amount = Input.get_action_strength("move_left")

# === TIMING ===

# delta
# Purpose: Time since last frame
# Usage: Multiply with velocity to keep motion smooth
# Formula:
position += velocity * delta

# yield / await
# Purpose: Pause code execution until something finishes
# Usage: Timers, animations, signal waits
# Formula:
await get_tree().create_timer(1).timeout

# Timer (Node)
# Purpose: Built-in time-based node
# Usage: Use with signals like timeout()
# Formula:
$Timer.start(2)
func _on_Timer_timeout():
    print("Done!")

# === SCENES ===

# preload
# Purpose: Load resource when the script runs
# Usage: Use for bullets, explosions, sounds, etc.
# Formula:
var Bullet = preload("res://Bullet.tscn")

# instance()
# Purpose: Create a new scene object
# Usage: Always use with preload
# Formula:
var bullet = Bullet.instance()
add_child(bullet)

# get_tree().change_scene()
# Purpose: Change to another scene
# Formula:
get_tree().change_scene("res://NextLevel.tscn")

# get_tree().reload_current_scene()
# Purpose: Restart the same scene
# Formula:
get_tree().reload_current_scene()

# === NODES ===

# get_node("Path") / $Node
# Purpose: Access a node in the scene
# Formula:
$Sprite.hide()

# add_child(node)
# Purpose: Add a new object to the scene tree
# Formula:
add_child(bullet)

# queue_free()
# Purpose: Delete a node safely
# Formula:
$Enemy.queue_free()

# === SIGNALS ===

# signal name
# Purpose: Declare a new custom event
# Formula:
signal exploded

# emit_signal("name")
# Purpose: Call that custom event
# Formula:
emit_signal("exploded")

# connect("signal", target, "method")
# Purpose: Link signal to a function
# Formula:
button.connect("pressed", self, "_on_Button_pressed")

# === DEBUG ===

# print()
# Purpose: Show info in console
# Formula:
print("Player HP:", hp)

# assert()
# Purpose: Crash game if condition is false
# Formula:
assert(score >= 0)

# push_error()
# Purpose: Log critical error without crash
# Formula:
push_error("Invalid value")
```

