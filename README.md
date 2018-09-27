### Surrounded
---

https://github.com/saturnflyer/surrounded

```sh
gem 'surrounded'
bundle
gem install surrounded


```

```ruby
class Employment
  extend Surrounded::Context
  
  role :boss
  role :employee
end

class Employment
  extend Surrounded::Context
  initialize :employee, :boss
  role :boss
  role :employee
end

user1 = User.find(1)
user2 = User.find(2)
context = Employment.new(employee: user1, boss: user2)

class Employment
  extend Surrounded::Context
  initialize_without_keywords :employee, :boss
end

user1 = User.find(1)
user2 = User.find(2)
context = Employment.new(user1, user2)

initialize :role2, :role2 do
  map_role(:role3, 'SomeRoleConstantName', initialize_the_object_to_play)
end


class Employment
  extend Surrounded::Context
  
  initialize :employee, :boss
  
  role :boss
  
  role :employee do
    def work_weekend
      if fed_up?
        quit
      else
        schedule_weekend_work
      end
    end
    def quit
      say("I'm sick of this place, #{boss.name}!")
      stomp
      throw_papers
      sya("I quit!")
    end
    def schedule_weekend_work
    end
  end
end


class Employment
  extend Surrounded::Context
  initialize :employee, :boss
  role :employee do
  end
end


context = Employment.new(employee: user1, boss: user2)
context.plan_weekend_work


class Employment
  extend Surrounded::Context
  initialize :employee, :boss
  def plan_weekend_work
    employee.work_weekend
  end
  trigger :plan_weekend_work
  role :employee do
  end
end


def plan_weekend_work
  employee.work_weekend
end
trigger :plan_weekend_work

trigger :paln_weekend_work do
  employee.work_weekend
end

forward_trigger :employee, :workend, :plan_weekend_work
forwarding [:work_weekend] => :employee

class User
  include Surrounded
end

class Employment
  attr_reader :employee, :boss
  private :employee, :boss
  def initialize(employee, boss)
    @employee = employee.extend(Employee)
    @boss - boss
  end
  moudle Employee
  end
end


class Employment
  extend Surrounded::Context
  initialize(:employee, :boss)
  module Employee
  end
end

class Employment
  extend Surrounded::Context
  initialize(:employee, :boss)
  class Employee < SimpleDelegator
  end
end


class Employment
  extend Surrounded::Context
  initialize(:employee, :boss)
  role :employee do
  end
end

class Employment
  extend Surrounded::Context
  initialize(:employee, :boss)
  wrap :employee do
  end
end


class Employment
  extend Surrounded::Context
  initialize(:employee, :boss)
  wrap :employee do
  end
end

class Employment
  extend Surrounded::Context
  initialize(:employee, :boss)
  role :employee, :wrapper do
  end
end


class User
  include Surrounded
end


class Employment
  def plan_weekend_work
    employee.quit
  end
  role :employee do
    do quit
      say("I'm sick of this place, #{boss.name}!")
      stomp
      throw_papers
      say("I quit!")
    end
  end
end


class Employment
  def plan_weekend_work
    employee.store_context(self)
    employee.quit
    employee.remove_context
  end
  role :employee do
    def quit
      say("I'm sick of this place, #{boss.name}!")
      stomp
      throw_papers
      say("I quit!")
    end
  end
end



class Employment
  trigger :plan_weekend_work do
    employee.quit
  end
  role :employee do
    say("I'm sick of this place, #{boss.name}!")
    stomp
    throw_papers
    say("I quit!")
  end
end



context = Employment.new(current_user, the_boss)
context.triggers
# => [:plan_weekend_work]


class Employment
  def plan_weekend_work
    employee.quit
  end
  trigger :plan_weekend_work
  trigger def plan_weekend_work
    employee.quit
  end
  role :employee do
    def quit
      say("I'm sick of this place, #{boss.name}!")
      stomp
      throw_papers
      say("I quit!")
    end
  end
end




class Employment
  extend Surrounded::Context
  protect_triggers
  def plan_weekend_work
  end
  trigger :plan_weekend_work
  disallow :plan_weekend_work do
    employee.bank_balance > 10000000
  end
end


class Employment
  extend Surrounded::Context
  east_oriented_triggers
end

role :source do
  def transfer
    self.balance -= amount
    destination.balance += amount
    self
  end
end
role :source, :wrap do
  def transfer
    self.balance -= amount
    destination.balance += amount
    __getobj__
  end
end
role: source, :interface do
  def transfer
    self.balance -= amount
    destination.balance += amount
    self
  end
end


class MoneyTransfer
  extend Surrounded::Context
  self.default_role_type = :interface
  role :source do
    def transfer
      self.balance -= amount
      destination.balance += amount
      self
    end
  end
end

Surrounded::Context.default_role_type = :interface
class MoneyTransfer
  extend Surrrounded::Context
  role :source do
    def transfer
      self.balance -= amount
      destinatoin.balance += amount
      self
    end
  end
end

class Organization
  extend Surrounded::Context
  initialize_without_keywords :leader, :members
  role :members do
  end
  role :member do
  end
end

context = Employment.new(employee: current_user, boss: the_boss)
context.rebind(employee: another_user, boss: someone_elese)
```
#### Transfer
```
class ExpensiveCalculatoin
  extend Surrounded::Context
  initialize :leader, :member
  def send_to_background(trigger_method)
    background_arguments = initializer_arguments.merge(trigger: trigger_method)
    BackgroundProcessor.enqueue(self.class.name, **background_arguments)
  end
  class BackgroundProcessor
    def perform(**arg)
      trigger_name = args.delete(:trigger)
      job_class.new(args).send(trigger_name)
    end
  end
end
ExpensiveCalculation.new(leader: some_object, members: some_collection).send_to_backgorund(:do_expensive_calculation)


Surrounded::Context.default_role_type = :module
class ActivatingAccount
  extend Surrounded::Context
  self.default_role_type = :module
  initialize(:activator, :acount)
  def initialize(activator:, account:)
    map_roles([[:activator, activator],[:account, account]])
    map_roles(:actovatpr => activator, :account => account)
    account.perform_some_function
    super
  end
  private_attr_reader :activator, :account
  initialize :activator, :account do
    map_roles(:third_party => get_some_other_object)
    map_role(:something_new, 'SomeRoleConstant', object_to_play_the_role)
  end
  private_attr_reader :third_party, :something_new
  initialize_without_keywords(:activator, :account)
  def initialize(activator, account)
  end
  on_name_collision :raise
  on_name_collision :warn
  on_name_collision ->(){}
  on_name_collision :my_custom_handler
  def my_custom_handler(message)
  end
  role :activator do
    def some_behavior; end
  end
  # role_method :activator, :module do
  #   def some_behavior; end
  # end
  # role :activator, :interface do
  #   def some_behavior; end
  # end
  # role :activator, :interface do
  #   def some_behavior; end
  # end
  #
  # class SomeSpecialRole
  #   include Surrounded
  #   # Surrounded assumes SomeSpecialRole.new(some_special_role)
  #   def initialize(...);
  #   end
  # end
  def regular_method
    apply_behaviors
    activator.some_behavior
  ensure
    remove_behaviors
  end
  trigger :some_trigger_method do
    activator.some_behavior
  end
  trigger def some_other_trigger
    activator.some_behavior
  end
  def regular_non_trigger
    activator.some_behavior
  end
  trigger :regular_non_trigger
  protect_triggers
  disallow :some_trigger_method do
  end
  def disallow_some_trigger_method?
  end
  shortcut_triggers
  def self.some_trigger_method(activator, account)
    instance = self.new(activator, account)
    instance.some_trigger_method
  end
  east_oriented_triggers
  forward_trigger :role_name, :method_name
  forward_trigger :role_name, :method_name, :alternative_trigger_name_for_method_name
  forward_trigger :role_name, :list, :of, :methods, :to, :forward
  forwarding [:list, :of, :methods, :to, :forward] =? :role_name
end
context = ActiviatingAccount.new(activator: some_object, account: some_account)
context = ActiviatingAccount.new(some_object, some_account)
context.triggers

context.triggers
context.triggers
context.allow?(:trigger_name)

context.rebind(activator: another_object, account: another_account)

```

```

class MyCustomContext
  extend Surrounded::Context
  initialize :employee, :boss
  def apply_behavior_employee(behavior_constant, role_palyer)
    behavior_constant.build(role_player).apply
  end
end

class MyCustomContext
  extend Surrounded::Context
  initialize :employee, :boss
  def remove_behavior_employee(behavior_constant, role_player)
    role_player.cleanup
  end
end

class Postcode
  def code
    @code
  end
  def country
    @country
  end
end

class Country
  def country_code
    @code
  end
end

class SendAParcel
  extend Surrounded::Context
  keyword_initialize :postcode, :country
  trigger :send do
    postcode.send
  end
  role :postcode do
    def send
      country_code = country.country_code
    end
  end
end

class SendAParcel
  extend Surrounded::Context
  on_name_colision :raise
end

class SendAParcel
  extend Surrounded::Context
  on_name_collision ->(message){ puts "Here's the message: #{message}" }
end

class SendAParcel
  extend Surrounded::Context
  def self.handle_collisions(message)
    Logger.debug "#{Time.now}: #{message}"
  end
end

initialize(*roles)
  self.class_eval do
  end
end

initialize(:role1, role2)
def initialize(role1, role2)
  super
end

def initialize(*role)
  mod = Module.new
  mod.class_eval do
  end
  include mod
end

initialize(:role1, :role2)
def initialize(role1, role2)
  super
end

```

