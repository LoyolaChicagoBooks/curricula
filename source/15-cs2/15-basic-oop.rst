Review of basic object-oriented programming
-------------------------------------------

Here is a simple example in Java that covers classes, records (introduced in Java 14), enums, constructors, accessors, mutators, and the use of `public` and `private` members:

First, we'll create an `enum` to represent a type of a pet:

.. code-block:: java

    public enum PetType {
        DOG,
        CAT,
        BIRD
    }


Next, we'll create a `class` to represent a Pet with fields, constructors, accessors, and mutators:

.. code-block:: java

    public class Pet {
        private String name;
        private PetType type;

        public Pet(final String name, final PetType type) {
            this.name = name;
            this.type = type;
        }

        public String getName() {
            return this.name;
        }

        public void setName(final String name) {
            this.name = name;
        }

        public PetType getType() {
            return this.type;
        }

        public void setType(final PetType type) {
            this.type = type;
        }

        @Override
        public String toString() {
            return "Pet{" +
                    "name='" + name + '\'' +
                    ", type=" + type +
                    '}';
        }
    }


Next, we'll create a `record` to represent an Owner. Records are a compact way to declare classes which are transparent holders for shallowly immutable data:

.. code-block:: java

    public record Owner(String name, String address) { }


Finally, we can create instances of our classes and manipulate them:

.. code-block:: java

    public class Main {
        public static void main(String[] args) {
            final var pet = new Pet("Fido", PetType.DOG);
            final var owner = new Owner("John Doe", "123 Main St");

            System.out.println(pet);
            System.out.println(owner);

            pet.setName("Spot");
            System.out.println(pet);
        }
    }


This example demonstrates encapsulation: the `Pet` class's `name` and `type` fields are `private`, so they can't be accessed directly from outside the class. Instead, they are accessed and modified through `public` accessor (getter) and mutator (setter) methods. The `Owner` record also demonstrates encapsulation, though in a different way: its fields are `public`, but they are `final` and can't be modified after the record is created. The `PetType` enum demonstrates a basic use of enums to represent a fixed set of values.


*Very nice and comprehensive. But why does Pet have a setType method? Can Fido become a cat?!?*

Great observation! In many real-world scenarios, some properties of an object might not change after its creation. In the case of a `Pet`, the `type` (whether it's a dog, cat, or bird) would realistically never change. Therefore, it would make more sense to omit the `setType` method to ensure the `type` field remains constant after the `Pet` object is created, which represents the concept of immutability.

Here's the adjusted `Pet` class:

.. code-block:: java

    public class Pet {
        private String name;
        private final PetType type;

        public Pet(final String name, final PetType type) {
            this.name = name;
            this.type = type;
        }

        public String getName() {
            return this.name;
        }

        public void setName(final String name) {
            this.name = name;
        }

        public PetType getType() {
            return this.type;
        }

        @Override
        public String toString() {
            return "Pet{" +
                    "name='" + name + '\'' +
                    ", type=" + type +
                    '}';
        }
    }


Now the `type` is marked as `final` and there's no `setType` method, meaning the `type` can't be changed after a `Pet` object is created. If you want to create a pet of a different type, you would need to create a new `Pet` object. This is more representative of the real world, where a pet's species can't change.
