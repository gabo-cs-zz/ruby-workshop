# Ruby Workshop

This is a brief Ruby guide, made with ♥.

## Installation

We'll install Ruby with some dependencies which we might need provided that we work with Rails.

- MAC OSX.

First, we need to install Homebrew. Homebrew allows us to install and compile software packages easily from source. Homebrew comes with a very simple install script. When it asks you to install XCode CommandLine Tools, say yes.

Open Terminal and run the following command:

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Now, let's go ahead and install Ruby. We're going to use rbenv to install and manage our Ruby versions.
```
brew install rbenv ruby-build

# Add rbenv to bash so that it loads every time you open a terminal
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
source ~/.bash_profile

# Install Ruby
rbenv install 2.6.3
rbenv global 2.6.3
ruby -v
```

- UBUNTU.

To make sure we have everything necessary for Webpacker support in Rails, we're first going to start by adding the Node.js and Yarn repositories to our system before installing them.

```
sudo apt install curl
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

sudo apt-get update
sudo apt-get install git-core zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev nodejs yarn
```

Next we're going to be using rvm to install and manage our Ruby versions.

```
sudo apt-get install libgdbm-dev libncurses5-dev automake libtool bison libffi-dev
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
curl -sSL https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm install 2.6.3
rvm use 2.6.3 --default
ruby -v
```

## How to run Ruby code

1. In IRB

   You can run `irb` in the terminal to launch a Ruby interpreter. You can see it as a playground to test things out.

2. Using Ruby files

   Using Ruby files, for example `wagon.rb`. Launch your Ruby script from the terminal with:

   ```bash
   ruby path/to/your/file.rb
   ````

## Built-in Ruby Objects

Everything in Ruby is an object. Objects have in-build methods you can call on them.

### Strings

- To represent text
- Defined with single quotes or double quotes: `'coding'` or `"coding"`

```ruby
"coding".class        # => String
"coding".capitalize   # => "Coding"
"coding".upcase       # => "CODING"
"CODING".downcase     # => "coding"

```

- With double-quoted strings, you can inject Ruby code into a string using interpolation or even use special characters.

```ruby
'two: #{1 + 1}'     # => "two: #{1 + 1}"
"two: #{1 + 1}"     # => "two: 2"

'It's raining'      # => syntax error, unexpected tIDENTIFIER
"It's raining"      # => "It's raining"

puts 'There\nis'    # => There\nis
puts "There\nis"    # => There
                         is

```

- You can convert strings to numbers

```ruby
'1984'.class         # => String
'1984'.to_i          # => 1984
'1984'.to_i.class    # => Integer
```

- You can convert strings to arrays

```ruby
'Ruby is an awesome language'.class         # => String
'Ruby is an awesome language'.split         # => ['Ruby', 'is', 'an', 'awesome', 'language']
```

### Integers

- To represent integers
- Can do standard arithmetic

```ruby
4.class              # => Integer
1 + 2                # => 3
2 * 4                # => 6
4 / 2                # => 2
2 ** 3               # => 8
2.next               # => 3
```

- Also has custom methods built-in

```ruby
20.even?             # => true
20.odd?              # => false
```

- You can convert numbers to strings

```ruby
1984.to_s          # => "1984"
```

### Floats

- To represent decimal numbers

```ruby
3.14.class         # => Float
1.23 + 2.1         # => 3.33
```

- Has it's own built-in methods

```ruby
3.14.round         # => 3
```

### Arrays

- To represent list of elements, usually of the same type
- Defined with square brackets around the list of items

```ruby
["paris", "london", "new york"].class     # => Array
[2, 5, 8, 2].class                        # => Array
[4.2, 5, "Hey", 12].class                 # => Array
```
- Has it's own built-in methods

```ruby
["paris", "london", "new york"].length    # => 3
["paris", "london", "new york"].sort      # => ["london", "new york", "paris"]
[3, 5, 1].sort                            # => [1, 3, 5]
```

- You can convert arrays to strings

```ruby
['Change', 'your', 'life'].class           # => Array
['Change', 'your', 'life'].join            # => "Changeyourlife"
['Change', 'your', 'life'].join(' ')       # => "Change your life"
```

- You access elements in an array based on its **index**

```ruby
saiyans = ["Goku", "Vegeta", "Trunks", "Gohan"]

saiyans[0]         # => "Goku"
saiyans[2]         # => "Trunks"

saiyans.first      # => "Goku"
saiyans.last       # => "Gohan"
saiyans[-1]        # => "Gohan"
```

- You add an element to an array by **appending** it or **inserting** it at a given **index**

```ruby
saiyans = ["Goku", "Vegeta", "Trunks", "Gohan"]

saiyans << "Goten"
p saiyans          # => ["Goku", "Vegeta", "Trunks", "Gohan", "Goten"]
```

- You modify an element in an array using its **index** again

```ruby
saiyans = ["Goku", "Vegeta", "Trunks", "Gohan"]

saiyans[1] = "Goten"
p saiyans          # => ["Goku", "Goten", "Trunks", "Gohan"]
```

- You delete an element from an array by using its **index** or by using its value

```ruby
saiyans = ["Goku", "Vegeta", "Trunks", "Gohan", "Goten"]

saiyans.delete_at(2)
saiyans.delete("Goten")
p saiyans          # => ["Goku", "Vegeta", "Gohan"]
```

### Booleans

- To represent something that is true or false


### DOCUMENTATION

The built in methods are well-documented, don't reinvent the wheel...

- [String methods](https://ruby-doc.org/core-2.3.3/String.html)
- [Fixnum methods](https://ruby-doc.org/core-2.3.3/Fixnum.html)
- [Floats methods](https://ruby-doc.org/core-2.3.3/Float.html)
- [Array methods](https://ruby-doc.org/core-2.3.3/Array.html)
- [Enumerable methods](https://ruby-doc.org/core-2.3.3/Enumerable.html)

## Comments
```ruby
# This is a single-line comment

# The following is a multi-line comment:

=begin
puts 'hey'
puts 'there'
=end
puts "what's up"
```

## Variables

- Allows you to store values to reuse them later
- You **assign** a value to a variables
- Variables can be overwritten and incremented

```ruby
age = 21
puts "You are #{age} years old"

age = age + 1
puts "You are now #{age}"
```

```ruby
first_name = "Alex"
last_name = "Benoit"

puts "My name is #{first_name} #{last_name}"
```

- By convention, variable names should be in snake_case (lowercase with underscores)


## Methods

- Concise way to call Ruby code multiple times
- Apply the ruby code to dynamic inputs
- Defined with **parameters** and called with **arguments**
- A method always returns a result, and you can then operate on what is returned

```ruby
def full_name(first_name, last_name)
  name = "#{first_name.capitalize} #{last_name.capitalize}"
  return name
end

puts full_name("albert", "einstein")  # => Albert Einstein
```

- In the example above, `first_name` and `last_name` were parameters and `"albert"` and `"einstein"` were the arguments, and we `puts` what returned from the method call
- We can call the method with variables too

```ruby
my_first_name = "nikola"
my_last_name = "tesla"
puts full_name(my_first_name, my_last_name)
```

Ruby reads your methods and looks for an implicit return, this means you don't need to type `return`, just place at the end what you want to be returned and that's it. The previous `full_name` method could be rewritten as follows:

```ruby
def full_name(first_name, last_name)
  "#{first_name.capitalize} #{last_name.capitalize}"
end
```
We also got rid of the `name` variable because we no longer need it.


- By convention, method names should be in snake_case (lowercase with underscores)
- By convention, methods ending with `?` such as `even?` and `start_with?` return a Boolean


## Flow Control

Conditionals and loops change the flow of a Ruby program. Conditionals allow us to execute a certain chunk of code under a specific condition. Loops allow us to execute a chunk of code multiple times. When the program is run, the code is executed from top to bottom, line by line, which is how you should debug in your head.

### Conditionals (If/Unless)

#### If

If conditionals allow us to execute a certain chunk of code if a condition is "thruthy".

```ruby
if condition
  # code executed only when condition is "truthy"
end
```

#### Unless

This statement is executed when the given condition is false. It is opposite of if statement.

```ruby
b = 0
b += 2 unless b.zero?
puts(b)
```

#### If/Else

If/Else conditionals allow us to execute a certain chunk of code if a condition is "thruthy" **or** another chunk of code if the same condition is **not** "truthy".

```ruby
if condition
  # code executed only when condition is "truthy"
else
  # code executed only when condition is not "truthy"
end
```

For example, a small Ruby program that checks if you are old enough to vote:

```ruby
puts "How old are you?"
age = gets.chomp.to_i

if age >= 18
  puts "You can vote!"
else
  puts "You cannot vote!"
end
```

### Simple loops

#### While

While loops allow us to execute a chunk of code multiple times while a condition is "truthy".

```ruby
while condition
  # executed while condition is truthy
end
```

For example, a small Ruby program that replicates the 'Price is Right' game.

```ruby
price_to_find = rand(1..5)
choice = 0 # or `nil`

while (choice != price_to_find)
  puts "How much (between 1 and 5)?"
  choice = gets.chomp.to_i
end

puts "You won!"
```

#### Until

Ruby <em>until loop</em> will execute the statements or code till the given condition evaluates to true. Basically it’s just opposite to the while loop.

```ruby
price_to_find = rand(1..5)
choice = 0 # or `nil`

until (choice == price_to_find)
  puts "How much (between 1 and 5)?"
  choice = gets.chomp.to_i
end

puts "You won!"
```

#### Do While
<em>do while</em> loop is similar to while loop with the only difference that it checks the condition after executing the statement.

```ruby
loop do
  puts "Enter a number"
  choice = gets.chomp.to_i
  break if choice == 3  
end
```

## OOP

Let's make a simple game to show some basics of OOP in Ruby.

```ruby
class Player
    attr_accessor :name, :health, :power
    def initialize(n, h, pow)
        @name = n
        @health = h
        @power = pow
    end
    def isAlive
        @health > 0
    end
    def hit(opponent)
        opponent.health -= self.power
    end
    def to_s
        "#{name}: Health: #{health}, Power: #{power}"
    end
end

def fight(p1, p2)
    while p1.isAlive && p2.isAlive
        p1.hit(p2)
        p2.hit(p1)
        
        show_info(p1, p2)
    end
    
    if p1.isAlive 
        puts "#{p1.name} WON!" 
    elsif p2.isAlive
        puts "#{p2.name} WON!" 
    else
        puts "TIE!"
    end
end

def show_info(*p)
    p.each { |x| puts x}
end

#initialize Players
puts "PLAYERS INFO"
p1 = Player.new("Player 1", 4, 5)
p2 = Player.new("Player 2", 5, 5)

#show Player info
show_info(p1, p2)

puts "LETS FIGHT!"
fight(p1, p2)
```
