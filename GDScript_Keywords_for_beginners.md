
# 📘 GDScript Keywords & Usage Guide

A compact, real-world dictionary of essential GDScript keywords.
Each entry includes purpose, usage rules, and a working example.

---

## 🎮 Movement & Input

### `move_and_slide(velocity)`
- **Purpose**: Moves a physics body with sliding support.
- **Usage**:
  - Call inside `_physics_process(delta)`
  - Needs a `velocity: Vector2` or `Vector3`
- **Formula**:
  ```gdscript
  velocity = Vector2(0, 100)
  velocity = move_and_slide(velocity)
  ```

### `Input.is_action_pressed("action_name")`
- **Purpose**: Checks if a key is being held.
- **Usage**: Inside `_process` or `_physics_process`
- **Formula**:
  ```gdscript
  if Input.is_action_pressed("ui_right"):
      velocity.x += 100
  ```

### `Input.is_action_just_pressed("action_name")`
- **Purpose**: Triggers once when key is pressed (not held).
- **Formula**:
  ```gdscript
  if Input.is_action_just_pressed("jump"):
      velocity.y = -200
  ```

---

## 📦 Nodes & Scene Management

### `get_node("NodePath")`
- **Purpose**: Access child or sibling nodes
- **Formula**:
  ```gdscript
  var my_node = get_node("Player/Sprite")
  ```

### `add_child(node)`
- **Purpose**: Adds a node to the current scene tree
- **Formula**:
  ```gdscript
  add_child(some_node_instance)
  ```

### `remove_child(node)`
- **Purpose**: Detaches node from parent
- **Formula**:
  ```gdscript
  remove_child(enemy)
  ```

### `queue_free()`
- **Purpose**: Deletes the node safely after current frame
- **Formula**:
  ```gdscript
  $Enemy.queue_free()
  ```

### `instance()`
- **Purpose**: Creates a copy of a PackedScene
- **Formula**:
  ```gdscript
  var BulletScene = preload("res://Bullet.tscn")
  var bullet = BulletScene.instance()
  add_child(bullet)
  ```

### `preload("res://path")`
- **Purpose**: Loads a scene or resource at compile time
- **Formula**:
  ```gdscript
  var Explosion = preload("res://Explosion.tscn")
  ```

---

## ⏳ Timing

### `yield(get_tree().create_timer(seconds), "timeout")`
- **Purpose**: Waits for a number of seconds (async)
- **Formula**:
  ```gdscript
  yield(get_tree().create_timer(2.0), "timeout")
  ```

### `Timer` node
- **Purpose**: Node-based timing
- **Formula**:
  ```gdscript
  $Timer.start(3)
  func _on_Timer_timeout():
      print("3 seconds passed")
  ```

### `delta`
- **Purpose**: Time difference between frames (for smooth movement)
- **Formula**:
  ```gdscript
  position += velocity * delta
  ```

---

## 🎲 Random

### `randomize()`
- **Purpose**: Initializes RNG, call once (e.g., `_ready()`)
- **Formula**:
  ```gdscript
  randomize()
  ```

### `randi()`
- **Purpose**: Returns a random int
- **Formula**:
  ```gdscript
  var x = randi() % 10  # 0-9
  ```

### `randf()`
- **Purpose**: Returns a float between 0 and 1
- **Formula**:
  ```gdscript
  var y = randf()
  ```

### `rand_range(a, b)`
- **Purpose**: Random float between a and b
- **Formula**:
  ```gdscript
  var speed = rand_range(100.0, 300.0)
  ```

---

## 📡 Signals & Checks

### `emit_signal("name")`
- **Purpose**: Emits a custom signal
- **Formula**:
  ```gdscript
  signal opened
  emit_signal("opened")
  ```

### `connect("signal", target, "method")`
- **Purpose**: Connects signals to a function
- **Formula**:
  ```gdscript
  button.connect("pressed", self, "_on_Button_pressed")
  ```

### `has_node("NodePath")`
- **Purpose**: Checks if the node exists
- **Formula**:
  ```gdscript
  if has_node("Enemy"):
      get_node("Enemy").queue_free()
  ```

### `is_instance_valid(node)`
- **Purpose**: Checks if a node reference still exists
- **Formula**:
  ```gdscript
  if is_instance_valid(enemy):
      enemy.queue_free()
  ```

---

👉 Add more as you need. Start building a living doc for yourself!
