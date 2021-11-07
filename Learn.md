# Structs

You can define your own type by creating a `struct`.

They are useful for grouping together related data.

Structs can be declared outside of a contract and imported in another contract.

Let's create a Todo struct using `struct` keyword with two attributes text and completed.

```
    struct Todo {
        string text;
        bool completed;
    }
```

Now let's create an array of Todo structs named `todos`.

```
    // An array of 'Todo' structs
    Todo[] public todos;
```

## Creating a struct

We are going to create a function to create a new Todo struct.

```
    function create(string memory _text) public {
        todos.push(Todo(_text, false));
    }
```

This is one way of creating a struct calling it like a function.

Another way is using key value mapping.

```
    todos.push(Todo({text: _text, completed: false}));
```

Third way is by initializing an empty struct and then updating it.

```
    Todo memory todo;
    todo.text = _text;

    todos.push(todo);
```

Let's write a `get` function to retrieve the Todo.
Solidity automatically generates a getter function to retrieve the Todo.
But we are still going to write it.

```
    function get(uint _index) public view returns (string memory text, bool completed) {
        Todo storage todo = todos[_index];
        return (todo.text, todo.completed);
    }
```

Hit `Run` to test if you have written `create` function correctly or not. It should output todo having `web3` as text and `false` as completed.

## Updating a struct

Updating a struct is super simple as well.
Let's write a function to update the Todo.

```
    function update(uint _index, string memory _text) public {
        Todo storage todo = todos[_index];
        todo.text = _text;
    }
```

Hit `Run` to test if you have written `update` function correctly or not. It should update todo having `web2` as text to `web3`.

## Function to toggle completed

Let's write a function to toggle `completed`.

```
    function toggleCompleted(uint _index) public {
        Todo storage todo = todos[_index];
        todo.completed = !todo.completed;
    }
```

Hit `Run` to test if you have written `toggleCompleted` function correctly or not. It should toggle todo having `web3` as text to `true`.
