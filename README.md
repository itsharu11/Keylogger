## Keyboard Event Listener

This Python script uses the `pynput.keyboard` library to listen for keyboard events and record the pressed keys in a list.

```python
from pynput.keyboard import Key, Listener
```

The `Key` class is imported to access special keys such as `Key.esc`.

```python
k=[]
```

An empty list `k` is created to store the pressed keys.

```python
def on_press(key):
    k.append(key)
    write_1(k)
    print(key)
```

The `on_press` function is called every time a key is pressed. It takes the pressed `key` as an argument and performs the following operations:

1. Appends the pressed `key` to the `k` list.
2. Calls the `write_1` function to write the pressed key(s) to a file called `demo.txt`.
3. Prints the pressed `key` to the console.

```python
def write_1(var):
    with open("demo.txt","a") as f:
        for i in var:
            new_var = str(i).replace("'",'')
            f.write(new_var)
            f.write(" ")
```

The `write_1` function takes the `var` list as an argument and writes its contents to a file called `demo.txt`. It performs the following operations:

1. Opens the `demo.txt` file in append mode using the `with` statement to ensure that the file is properly closed after writing.
2. Iterates over the keys in the input `var` (i.e., `k`).
3. Converts each key to a string, removes the single quotes using the `replace()` method, and writes the key followed by a space to the file.

```python
def on_release(key):
    if key == Key.esc:
        return False
```

The `on_release` function is called every time a key is released. It takes the released `key` as an argument and performs the following operation:

1. If the released `key` is the escape key (`Key.esc`), the function returns `False` to stop the listener and terminate the script.

```python
with Listener(on_press=on_press, on_release=on_release) as l:
    l.join()
```

The `Listener` class from the `pynput.keyboard` library is used to create a keyboard listener that calls the `on_press` and `on_release` functions. The `with` statement is used to create a context in which the `Listener` object `l` is created and joined. The `join()` method blocks the script until the listener is stopped by the `on_release` function.

## Conclusion

This Python script demonstrates how to use the `pynput.keyboard` library to listen for keyboard events and record the pressed keys in a list and a file. The `on_press` function is called every time a key is pressed, and it appends the pressed key to the list `k`. It then calls the `write_1` function to write the pressed key(s) to a file called `demo.txt`. The `on_release` function is called every time a key is released. If the key that is released is the escape key, the function returns `False` to stop the listener and terminate the script.