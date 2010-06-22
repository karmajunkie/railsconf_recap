!SLIDE 
#RailsConf 2010 Recap#
##Keith Gaddis##
###keith@collectiveidea.com / @karmajunkie###
###Collective Idea###

!SLIDE bullets incremental
#Themes this year#
* We are **AWESOME**
* Rails 3 is **AWESOME**
* NoSQL is **AWESOME**
* Most people don't know this but JRuby is **AWESOME**

!SLIDE bullets incremental
#What did I learn overall?#
* The in-crowd and rockstars aren't much smarter than the rest of us
* They just work harder
* Get out an interact as much as possible 
* (*Watch out for the free drink tickets!*)
* (*See you at B.D. Reilly's!*)

!SLIDE bullets incremental
#What else did I learn?#
* We have a big problem
* Too many job openings!
* Not enough experienced Rails developers
* Community needs to work harder at being inclusive for n00bs

!SLIDE bullets incremental
#Notable Keynotes
* DHH
* Michael Feathers, ObjectMentor
* Katz
* Gary Vaynerchuk

!SLIDE smbullets incremental
#DHH
* What's exciting in Rails 3 (to him)
* Bundler
* AREL
* Routing Refactor
* ActionMailer rewrite
* Takeaway message: We're solving harder problems with simpler code

!SLIDE code 
#bundler
    source "http://rubygems.org"
    gem "nokogiri"
    gem "rack", "~>1.1"
    gem "rspec", :require => "spec"

!SLIDE commandline incremental smaller
#bundler
    $ bundle install
    Fetching source index from http://rubygems.org/
    Installing nokogiri (1.4.2) from rubygems repository at http://rubygems.org/ with native extensions 
    Installing rack (1.2.1) from rubygems repository at http://rubygems.org/ 
    Installing rspec (1.3.0) from rubygems repository at http://rubygems.org/ 
    Your bundle is complete! Use `bundle show [gemname]` to see where a bundled gem is installed.

!SLIDE code incremental smaller
#ARel
    lifo = User.where(:name => 'lifo')
    new_users = User.order('users.id DESC').limit(20)
    
!SLIDE bullets incremental
#Michael Feathers, ObjectMentor
##Working with legacy code
* Do we have legacy code in the Rails community? (Yes.)
* Do you write good code (Probably not.)
* What makes good code?
* What's a Big Ball of Mud?

!SLIDE bullets incremental
#Michael Feathers, ObjectMentor
* Can we fight entropy?
* Tests matter a lot more in code that changes a lot
* You can use repos to figure out those areas (more later)

!SLIDE bullets incremental
#Yehuda Katz, EngineYard
##The Ruby community
* Intimidated? _Watch this keynote!_
* Anybody can be AWESOME
* Getting involved can seem hard because of the 'in-crowd' notion
* The 'In-Crowd' is an artificial distinction

!SLIDE bullets incremental
#Yehuda Katz: Ruby Community
* We have to be more inclusive
* RTFM doesn't do the n00b any good because they don't know what they're looking for
* To get involved: do something
* Even if it seems impossible
* Just *work hard*

!SLIDE bullets incremental
#Gary Vaynerchuk
* he swears a lot
* but its ok because he's passionate
* he also likes hugs from the audience
* I can't do this justice

!SLIDE incremental bullets
#Gary Vaynerchuk
* QOTD:"Giving a F*ck is coming on strong" 
* Companies have to connect to customers in a way that makes them feel cared about
* "Thank You Economy"

!SLIDE title
#Talks I found worthwhile
## (way too many)

!SLIDE bullets incremental
#Don't Repeat Yourself—Repeat Others
##John Nunemaker, OrderedList
* John writes a lot of popular libraries
* HTTParty, HappyMapper, crack, MongoMapper
* John's theme: I'm not smart, I just work hard
* (He's smarter than he'll admit to...)

!SLIDE bullets incremental
#John Nunemaker, Don't Repeat Yourself
* Reinvent the wheel: You learn from it
* Eat your own Dogfood (API's), 
* learn the design patterns in the community
* Don't be afraid to steal code
* Write about it

!SLIDE bullets incremental
#Rocket Fueled Cucumbers
##Joseph Wilk, Songkick.com
* Using cucumber doesn't mean every test run has to take an hour
* Strategies for speeding things up

!SLIDE smbullets incremental
##Joseph Wilk, Rocket-Fueled Cucumbers
* focused cukes
* use tags, directories, single files, single scenarios
* spork: load the overhead once
* tag scenarios that use slow services (i.e. search) and use a Before block to do slow stuff
* cucover: autospec for cucumber (early in development, but working!)

!SLIDE smbullets incremental
##Joseph Wilk, Rocket-Fueled Cucumbers
##Testjour: distributed test suite
* takes some work to configure (See Ethan Waldo's March presentation for example)
* Songkick uses with EC2 servers (20)
* reduces 4 hour build time to 11.6 mins
* Expensive!
* use slim-sumo to launch EC2 servers on demand

!SLIDE bullets incremental
##Joseph Wilk, Rocket-Fueled Cucumbers
##Hydra
* Another distributed test suite
* can run rspec, Test::Unit, and Cucumber
* Aimed at maximizing use of multicore processors as well as distributed build

!SLIDE bullets incremental
##Joseph Wilk, Rocket-Fueled Cucumbers
##Run tests that matter
* Not all tests are created equal (or equally likely to fail)
* run likely failures in the CI build (every checkin)
* run full suite in nightly build

!SLIDE bullets incremental
##Joseph Wilk, Rocket-Fueled Cucumbers
##Architectural segmentation
* use SOA to modularize code
* smaller, more focused suites

!SLIDE smbullets incremental
#12 hours to rate a Rails app
##Elise Huard, Jabberwocky
* Whether you're taking over an application or dealing with your own, we need ways to assess the health of a codebase

!SLIDE smbullets incremental
##Areas to check
* Team
* App
* Metrics
* Database
* Views
* Deployment

!SLIDE bullets incremental
#Team
*	Roles of team members
*	Vision
*	Methodology
*	bug tracking
*	version 

!SLIDE smbullets incremental
#App
*	Try it out - Does it work?
*	Rails version
*	Plugins/gems
*	how does it manage updates (bundler, piston, submodules, etc?)
*	Licenses?
*	Tests (please say you have tests!)
*	Routing - Lots of named routes vs restful resources

!SLIDE smbullets incremental
#Metrics
*	rake stats => LOC
*	flog - detects & rates code complexity: you want score < 50 (<20 is great)
*	flay - detects code similarities: lower score is better
*	saikuro - another complexity tool
*	roodi - Ruby Object Oriented Design Inferometer (looks for code smells and complexity)
*	reek - code smells

!SLIDE smbullets incremental
#Metrics, con't
*	rails_best_practices - gives BP suggestions
*	churn - looks for code that changes a lot (use to focus tests?)
*	rcov
*	heckle - changes the data and functions your tests use.  Ideally they all break when heckle's through with them
*	metric_fu - wraps up a lot of these into a single gem
*	(None of these will detect outright bugs)

!SLIDE bullets incremental
#Database
*	schema.rb
*	seed data
*	migrations

!SLIDE bullets incremental
#View
*	indentation
*	div-itis
* misplaced code

!SLIDE bullets incremental
#Deployment
*	should be completely automated

!SLIDE title
#Thanks
##Keith Gaddis##
###keith@collectiveidea.com / @karmajunkie###
###Collective Idea###
###http://github.com/karmajunkie/railsconf_recap###
