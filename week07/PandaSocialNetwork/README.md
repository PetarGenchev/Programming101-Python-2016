# We are going to make a social network for Pandas

This is the next big thing. We promise!

## Panda

For our social network, we are going to need a `Panda` class which should behave like this:

```python
ivo = Panda("Ivo", "ivo@pandamail.com", "male")

ivo.name() == "Ivo" # True
ivo.email() == "ivo@pandamail.com"  # True
ivo.gender() == "male" # True
ivo.isMale() == True # True
ivo.isFemale() == False # True
```

The `Panda` class should also:

* Be turned into a string
* Be hashed and used as a key in a dictionary (`__eq__` and `__hash__`)
* **Make sure that the `email` is a valid email!**

Two `Panda` instances are equal if they have matching `name`, `email` and `gender` attributes.

## SocialNetwork

Now it is time for our social network!

Implement a class, called `PandaSocialNetwork`, which has the following public methods:

* `add_panda(panda)` - this method adds a `panda` to the social network. The panda has 0 friends for now. If the panda is already in the network, raise an `PandaAlreadyThere` error.
* `has_panda(panda)` - returns `True` or `False` if the `panda` is in the network or not.
* `make_friends(panda1, panda2)` - makes the two pandas friends. Raise `PandasAlreadyFriends` if they are already friends. **The friendship is two-ways** - `panda1` is a friend with `panda2` and `panda2` is a friend with `panda1`. **If `panda1` or `panda2` are not members of the network, add them!**
* `are_friends(panda1, panda2)` - returns `True` if the pandas are friends. Otherwise, `False`
* `friends_of(panda)` - returns a list of `Panda` with the friends of the given `panda`. Returns `False` if the `panda` is not a member of the network.
* `connection_level(panda1, panda2)` - returns the connection level between `panda1` and `panda2`. If they are friends, the level is 1. Otherwise, count the number of friends you need to go through from `panda` in order to get to `panda2`. If they are not connected at all, return `-1`! Return `False` if one of the pandas are not member of the network.
* `are_connected(panda1, panda2)` - return `True` if the pandas are connected somehow, between friends, or `False` otherwise.
* `how_many_gender_in_network(level, panda, gender)` - returns the number of pandas with gender `gender` (male of female) that are in the `panda` network in `level` levels deep. If `level == 2`, we will have to look in all friends of `panda` and all of their friends too. And count

## An example

```python
network = PandaSocialNetwork()
ivo = Panda("Ivo", "ivo@pandamail.com", "male")
rado = Panda("Rado", "rado@pandamail.com", "male")
tony = Panda("Tony", "tony@pandamail.com", "female")

for panda in [ivo, rado, tony]:
    network.add(panda)

network.make_friends(ivo, rado)
network.make_friends(rado, tony)

network.connection_level(ivo, rado) == 1 # True
network.connection_level(ivo, tony) == 2 # True

network.how_many_gender_in_network(1, rado, "female") == 1 # True
```


## Save and load from file

The next thing our social network is going to do is ``saving to your hard drive``.

### social_network.save(file_name)

Write a function that saves the whole social network to a file. The format of that file is not important but you have to be able to load it in the program. So all the data in the network must be written down to that file.

### social_network.load(file_name)

Write a function that loads the whole social network from a file. All the pandas and all the relations.
