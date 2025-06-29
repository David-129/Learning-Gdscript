```gdscript
# 📘 GDScript Keywords - Keyword + Purpose + Formula + Usage Rule
# A compact, real-world dictionary of essential GDScript keywords with clear purposes.

# === VARIABLES & TYPES ===
# var - Declare a mutable variable
# const - Declare a constant (immutable)
# export - Make variable visible/editable in the editor
# onready - Assign after node is fully ready in scene tree
# class_name - Allow global use of the class name
# extends - Inherit another class or Node

# EXAMPLE:
const GRAVITY = 400           # Constant value
export var speed := 200      # Editable in the inspector
onready var cam = $Camera2D  # Available only after scene is ready
class_name Player            # Can be used as Player.new()
extends CharacterBody2D     # Inherit from CharacterBody2D

# === CONTROL FLOW ===
# if / elif / else - Conditional branching
# match - Switch-case-like comparison
# for / while - Loops (range/array/condition)
# break / continue - Control loop behavior
# return - Exit function early

if hp <= 0:
    die()
elif hp < 20:
    warn()
else:
    idle()

match input:
    "left": move_left()
    "right": move_right()

for i in range(5):
    print(i)

while hp > 0:
    regen()

# === FUNCTIONS & SIGNALS ===
# func - Define a function
# signal - Declare a custom event
# emit_signal() - Fire your custom signal
# await / yield - Pause execution until condition/timer/signal completes

signal shot_fired
func shoot():
    emit_signal("shot_fired")
    await get_tree().create_timer(0.3).timeout
    print("Bang!")

# === INPUT ===
# Input.is_action_pressed() - Hold detection
# Input.is_action_just_pressed() - One-time press detection
# Input.get_action_strength() - Get analog/combined strength (e.g., for controllers)

if Input.is_action_pressed("ui_up"):
    velocity.y -= speed

# === NODES ===
# get_node(path) or $NodePath - Access another node
# add_child(node) - Add node as child
# remove_child(node) - Remove child node
# queue_free() - Delete node safely
# get_parent() - Get the parent node
# get_tree() - Access the SceneTree

$Label.text = "Game Over"
add_child(instance)
get_node("Player/Sprite").hide()
get_parent().remove_child(self)

# === INSTANCING & RESOURCES ===
# preload(path) - Compile-time loading
# load(path) - Runtime loading
# instance() - Create a copy of a PackedScene

var BulletScene = preload("res://Bullet.tscn")
var bullet = BulletScene.instance()
bullet.position = position
add_child(bullet)

# === SCENE TREE ===
# get_tree().change_scene(path) - Change to a new scene
# get_tree().quit() - Quit the game
# get_tree().reload_current_scene() - Restart current scene

get_tree().change_scene("res://GameOver.tscn")

# === TIMING ===
# delta - Time between frames (used for smooth movement)
# Timer - Node-based timer
# await/yield get_tree().create_timer(seconds).timeout - Delay execution

position += velocity * delta
await get_tree().create_timer(1.5).timeout

# === RANDOM ===
# randomize() - Call once at game start
# randi() - Random integer
# randf() - Float between 0-1
# rand_range(a, b) - Float between a and b

randomize()
var index = randi() % 4
var chance = randf()
var damage = rand_range(5.0, 15.0)

# === SIGNALS ===
# signal name - Define event
# emit_signal("name") - Call it
# connect("signal", target, "method") - Connect it manually

signal opened
emit_signal("opened")
$Door.connect("opened", self, "_on_Door_opened")

# === DEBUG ===
# print(), push_error(), assert()

print("HP: ", hp)
push_error("Enemy not found")
assert(hp >= 0)

# === GROUPS & VALIDITY ===
# is_instance_valid(node) - Node still exists?
# has_node(path) - Node exists?
# is_in_group(name) - Node belongs to group?

if is_instance_valid(enemy):
    enemy.queue_free()

if has_node("Boss"):
    get_node("Boss").start_fight()

if is_in_group("enemies"):
    take_damage()

# === COLLISION & PHYSICS ===
# move_and_slide() - Slide movement for physics bodies
# move_and_collide() - Stop on first collision
# is_on_floor() - Check grounded status

velocity = move_and_slide(velocity)
if is_on_floor():
    jump_available = true

# === COLLECTIONS ===
# Arrays: []
# Dictionaries: {}
# .append(), .erase(), .size(), .keys(), .values()

var list = ["a", "b"]
list.append("c")
var dict = {"hp": 100}
dict["hp"] -= 10

# === COMBINABLE STRUCTURE EXAMPLES ===

# Example 1: preload + instance + input + add_child + move
var BulletScene = preload("res://Bullet.tscn")
if Input.is_action_just_pressed("shoot"):
    var b = BulletScene.instance()
    b.position = position
    add_child(b)

# Example 2: signal + connect + await
signal exploded
func trigger():
    emit_signal("exploded")
    await get_tree().create_timer(2).timeout
    queue_free()

# Example 3: array loop
var items = ["potion", "sword"]
for i in items:
    print(i)

# Example 4: match input strength
match Input.get_action_strength("move_dir"):
    1.0:
        move_fast()
    _:
        move_slow()
```
