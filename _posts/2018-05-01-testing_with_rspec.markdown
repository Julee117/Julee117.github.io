---
layout: post
title:      "Testing with RSpec"
date:       2018-05-02 03:40:42 +0000
permalink:  testing_with_rspec
---


Testing is one of the things that I will be working on while building new apps to further my skills as a developer. I have read in many blogs that it is perceived writing tests takes too much time. However, it is helpful in verifying our codes function as intended. We also gain time by not having to manually check our codes. 

Test-Driven-Development uses a red, green, refactor approach which is: 
- Red – Write a test that fails 
- Green - Write a code that passes the test 
- Refactor - When the test pass, clean up the code 

### Setting Up RSpec

First add the gem to your Gemfile:
```
gem ‘rspec-rails’
```

Add a spec folder:
```
bundle install 
bundle exec rails g rspec:install 
```

### Basic Syntax

`describe` is RSpec’s unit of organization and gathers together several `it` blocks into a single unit. `describe` and `it` take strings as arguments. For `describe`, use the name of the method you are testing.  Use “.” when testing a class method and “#” when testing an instance method. `describe` can also take a constant that is the name of the class or model you are testing. 

```
describe Student do 
  describe ".student_class_method" do 
  end 
	
  describe "#student_instance_method" do 
  end 
end
```

For `it`, you describe the behavior you are testing.

`expect()` matches between the value your code returns and the expected value. 

```
describe "hello" do 
  it "says hello" do
    expect(hello).to eq("Hello!")
  end
end 
```

`context` is an alias method of `describe`. They both group related tests together. `context` names should explain why or when a user would call the method.

```
describe "#new" do 
  contect "when logged in" do 
  end 
end 
```

`let` is a standard helper method that takes a symbol and a block. It is not evaluated until the method is run for the first time. It also does not persist state so the same value is returned when the method is invoked within the same scope. Every `it` is a different scope so `let` does not persist state between them.   

```
describe “Dog” do 
  let(:dog) { Dog.new(“Cooper”)}

  describe “name” do 
    it “returns a new name” do 
      dog.name = “Benji” 
      expect(dog.name).to eq(“Benji”)
    end 

    it “returns original value” do 
      expect(dog.name).to eq(“Cooper”)
    end 
  end 
end 
```

There is much more to RSpec than this. Further information can be found in [RSpec docs](https://relishapp.com/rspec/rspec-core/v/2-4/docs).





