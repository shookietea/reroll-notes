# Bot commands

## `!size`

`!size [name]` prints the size of all objects matching `[name]`. The search tries to correct for minor spelling differences between your search and the game’s names. The objects containing the whole string `[name]` are also returned.

```
!size dog

Log: 1m32cm4mm | Dogfood Bowl: 30cm4mm | Doggy: 59cm6mm | Dog With Fleas: 1m10cm1mm | Bulldog: 94cm3mm | Toy Dog: 40cm8mm | Doghouse: 1m42cm1mm
```

## `!calc`

The `!calc` command computes a katamari’s new size after objects are either added or removed. The command needs four arguments:
- A game level (this is necessary since the game’s size formula depends on the level)
- The katamari’s initial size
- Either a `+` or `-` to indicate if you’re adding or removing objects
- A comma-separated list of objects to add or remove

If the bot successfully parses the command, the computed final size will be shown in double brackets. 

Subtraction calcs are useful in situations where you’d like to know in advance you’ll be a certain size after picking up specific objects. For example, the following calc says you need to be at least 4m7cm1mm to end up at Small Tree size after picking up a Park Lamp Post and a Flower Bed (as applied in [this IL](https://youtu.be/lCjwJYOH-JE?t=77)):

```
!calc mas7: small tree - flower bed, park lamp post

(MAS7): [[4m7cm0.1388mm]] + Flower Bed(x1), Park Lamp Post(x1) = Small Tree (4m18cm)
```

### Useful shortcuts
- If the katamari’s initial size is an object’s pickup size, you can use the object’s name instead of its numeric size.

- You can include more than one of the same object with `x` followed by the quantity:

```
!calc mas8: brick - ham x5, piggybank

(MAS8): [[36cm3.406mm]] + Ham(x5), Piggybank(x1) = Brick (40cm9mm)
```

## Nametags

KD contains quite a few __ambiguous__ object names shared by more than one distinct object. In both the practice mod and bot, ambiguous object names are always followed by a __name tag__ in square brackets that clarifies which object is meant:

```
!size bucket

Bucket [Can]: 1m26cm2mm | Bucket [Small]: 77cm5mm
``` 

These name tags can also be used in your own bot commands where you need to refer to an ambiguously named object:

```
!calc mas4: cucumber plant - bucket [small] x3

(MAS4): [[81cm3.277mm]] + Bucket [Small] (x3) = Cucumber Plant (85cm3mm)
```
