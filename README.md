# dcontain
DContain is a small utility library containing various container types.

Containers are under the `containers` module

## Example

```d
import containers;
import std.stdio;

struct User {
    string firstname;
    string lastname;
    size_t id;
}

void main() {
    User eve = User("Eve", "", 3);
    List!User users = [
        User("John", "Doe", 0),
        User("Alice", "", 1),
        User("Bob", "", 2)
    ];

    users ~= eve;
    
    // Remove Bob
    users.removeAt(2);
    
    /// should output the lists contents without bob.
    writeln(users);

    /// Reverse users list and print again
    users.reverse();
    writeln(users);
    users.reverse();

    /// Remove Eve
    users.remove(eve);
    writeln(users);

    /// Foreach loops
    foreach(user; users) {
    	writeln(user);   
    }
    
    /// Getting index also works!
    foreach_reverse(i, user; users) {
    	writeln(i, ": ", user);   
    }
}
```

#### Output
```
[User("John", "Doe", 0), User("Alice", "", 1), User("Eve", "", 3)]
[User("Eve", "", 3), User("Alice", "", 1), User("John", "Doe", 0)]
[User("John", "Doe", 0), User("Alice", "", 1)]
User("John", "Doe", 0)
User("Alice", "", 1)
1: User("Alice", "", 1)
0: User("John", "Doe", 0)
```