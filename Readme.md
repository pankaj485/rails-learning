### [learning resource](https://www.youtube.com/watch?v=fmyvWz5TUWg&t=11122s)

# Rails note

[pre-requisites](#pre-requisites)

[Setup](#setup)

[creating project](#creating-project)

[running project](#running-project)

[gemfile](#gemfile)

[MVC architecture](#mvc-architecture)

[directories in the project](#directories-in-the-project)

[generator in rails](#generator-in-rails)

[changing routes in rails](#changing-routes-in-rails)

[Application partial links and new pages](#application-partial-links-and-new-pages)

[creating files by self without generator](#creating-files-by-self-without-generator)

[adding bootstrap to our project](#adding-bootstrap-to-our-project)

[creating link to partial](#creating-link-to-partial)

[using links in rails](#using-links-in-rails)

[CRUD Scaffold](#crud-scaffold)

[Styling App with Bootstrap](#styling-app-with-bootstrap)

[Devise User Management](#devise-user-management)

[verify signin and show particular contents acc to authentication](#verify-signin-and-show-particular-contents-acc-to-authentication)

[Style Devise Views](#style-devise-views)

[Associations](#associations)

[associate/connect friends and users table present at `app>models>firend.rb` and `app>models>user.rb` files](#associateconnect-friends-and-users-table-present-at-appmodelsfirendrb-and-appmodelsuserrb-files)

[prepopulate `user_id` while creating data (creating friends in course)](#prepopulate-user_id-while-creating-data-creating-friends-in-course)

[More associations](#more-associations)

[associate data according to user](#associate-data--according-to-user)

# pre-requisites

- node
- ruby
- gem
- rails
- sqlite3
- rvm
- yarn

# Setup

## creating project

```markdown
1. rails new <project_name>
2. cd <project_name>
3. rails server
```

## running project

```
http://localhost:3000/
```

# gemfile

- allows to install various file in app

# MVC architecture

- stands for model view controller
- model : databasaes
- view : webpages
- controller : brain behind the scene

## directories in the project

app directory

- assets directory : includes html, css, js files
- controllers dir : c in mvc
- javascript dir : js dir
- models : m in mvc
- views : v in mvc

config

- consist of configuration files

gemfile

- includes gem infos

## generator in rails

- generator allows to generate things for the webpage
- creating a controller in home directory along with creating a .html.erb page called index
- g is acronym for generate
  ```
  rails g controller home index
  ```
- .html.erb means embeded ruby

## changing routes in rails

- navigate to config>routes.rb file
- use command:
  ```
  root "home#index"
  ```
- since the route is for the root route "#" is used instead of "/"
- "home" route is coming from "app>views>"

# Application partial links and new pages

- partial is kind of concept of component in rails which are partial part of page
- partial can be used in every route of the website (e.g header, footer)
- partial files are started with "\_" like `_about.html.erb`
- app>views>layouts>application.html.erb file contains the base template code
- `<%= yeild %>` is used to add up all the created other sets of code and rest of it incl title, header and other contents will be same for all the routes except of the contents added inside of `<%= yeild %>`
- concept of yeild is kind of similar to concept of components in react to relate to

## creating files by self without generator

1. creating view

   ```
   navigate to: app>views>home>
   rightclick and create: <file_name>.html.erb file
   ```

2. creating controller

   ```
   navigate to: app>controllers>home_controller.rb
   add: def <file_name>
   			end
   ```

3. creating route

   ```
   navigate to: config>routes.rb
   add: get 'home/<file_name>'
   ```

## adding bootstrap to our project

- adding bootstrap is simple and so much similar to normal way
- to add bootstrap:
  ```
  1. cd app>views>layouts>application.html.erb
  2. add respective css and javascript codes in header and body respectively
  ```

## creating link to partial

- creating partial pages:
  - navigate to `app>home>_<file_name>` (file name starts with "\_")
- navigate to `app>views>layouts>application.html.rb`
- add the tag `<%= render 'home/<file_name_without_underscore>' %>`
- <%= %> is embeded ruby tag
  - <%= %> means to embed the partial to screen
  - <% %> means to not to embed the partial to screen (i.e using if else statements)

## using links in rails

- taking example of the code below:

1. case 1

   ```jsx
   <%= link_to 'Friend_App', root_path, class:"navbar-brand" %>
   ```

- embeded tags are used here
  - `link_to` is like anchor tag in html which means we are using a link just like "<a>" tag
  - `"Friend_App"` is the placeholder for the link or simply link name
  - `root_path` is the home page opening on [localhost:3000/](http://localhost:3000/) which serves as
  - `class:"navbar-brand"` is the class provided to the link
- only for`root_path`tag is used like this since it is for root

1. case 2

   ```jsx
   <%= link_to "About Us", home_about_path, class:"nav-link"  %>
   ```

- concepts are almost same, different ones are written below:
  - `home_about_path` actually means:
    - `home`: the directory where page to link is present which is usually in `app>views>`
    - `_about`: is the file name present in the directory
    - `_path`: is usually used after the file name (prefix) and no such use cases is talked by instructor

# CRUD Scaffold

- crud is easy for rails comparing to other techs
- CRUD stands for Craete, Read, Update, Delete
- scaffold is used in rails for crud operations
- example to generate scaffold:

  ```ruby
  	rails g scaffold friends first_name:string last_name:string emial:string phone:string
  ```

- doing it will create the model/table/schema logically but it's not live yet
- it will create routes, controllers, css files and many other things
- scaffold css file may cause styling issues if so it can be deleted from `app>assets>stylesheets><scaffolds.scss>`
- `rails g scaffold` is creating a scaffold for database model/table/schema called as `friends`
- `first_name:string` is creating attribute (column) called first_name with string data type
- the model/table/schema can be located in `db>migrate><some_codes__create__modal_name.rb>`
- pushing/migrating created migrations into databases live:
  ```ruby
  rails db:migrate
  ```
- the command will create `schema.rb` file in `db>` directory
- inside of `config>routes.rb` automated route is set up by rails as `resources :<schema_name>` , which can be treated as route
- after this we can navigate to `[localhost:3000/<schema_name>](http://localhost:3000/<schema_name>)` to see the db and explore various options created by scaffold which helps on fully functional crud interface
- to add the route created by scaffold:
  ```ruby
  <%= link_to "<label>", <route_name>_path, class:"" %>
  ```
  - in course it's used as:
    ```ruby
    <%= link_to "Friends", friends_path, class:"nav-link"   %>
    <%= link_to "New Friend", new_friend_path, class:"nav-link"   %>
    ```

# Styling App with Bootstrap

- standard way of using bootstrap

# Devise User Management

- devise is gem
- gem is bundle
- using devise gem:
  1. go to doc and and it to Gemfile as `gem 'devise', '~> 4.8'`
  2. go to terminal and execute `bundle install`
  3. execute `rails generate devise:install`
  4. follow the commands
     1. setup environment files
  5. run `rails g devise:views` to create essential VIEWS files
  - it will create all required files just like scaffold
  1. run `rails generate devise <model_name>` to create MODEL of `<model_name>`
  2. run `rails db:migrate` to push migrations
- lots of good things are present in documentation so go and explore it also
- while using `DELETE` route make sure to use `method: :delete` for delete route like signout

### verify signin and show particular contents acc to authentication

- this can be achieved using `user_signed_in?` helper from devise itself
- it can be used with embeded rails to show contents acc to the situations
- example:

  ```html
  <ul class="navbar-nav me-auto mb-2 mb-lg-0">
  	<li class="nav-item">
  		<!-- <a class="nav-link" href="#">Link</a> -->
  		<%= link_to "About Us", home_about_path, class:"nav-link" %>
  	</li>

  	<% if user_signed_in? %>
  	<li class="nav-item">
  		<%= link_to "Sign Out", destroy_user_session_path, method: :delete,
  		class:"nav-link" %>
  		<!-- method: :delete is used since this is delete request form route note the way space is used between colons   -->
  	</li>
  	<li class="nav-item">
  		<%= link_to "Edit Profile", edit_user_registration_path, class:"nav-link"
  		%>
  	</li>
  	<% else %>
  	<li class="nav-item">
  		<%= link_to "Sign Up", new_user_registration_path, class:"nav-link" %>
  	</li>
  	<li class="nav-item">
  		<%= link_to "Sign In", new_user_session_path, class:"nav-link" %>
  	</li>

  	<% end %>
  </ul>
  ```

# Style Devise Views

- standard way of using bootstrap

# Associations

- association is a way to associate/connect various databases (in course context users table and friends table )
- to associate one db to another we use `belongs_to` , `has_many` kind of associations [documentation link](https://guides.rubyonrails.org/association_basics.html)
- before associating databases we need to clear all the previous datas of databases since they are not associated previously

### associate/connect friends and users table present at app>models>firend.rb and app>models>user.rb files

- each user has friends and each fiend belogs to a user we are going to asociate the relations of them now
- for `friend.rb` file:
  ```ruby
  class Friend < ApplicationRecord
  	belongs_to :user
  end
  ```
- for `users.rb` file:
  ```ruby
  class User < ApplicationRecord
    # Include default devise modules. Others available are:
    # :confirmable, :lockable, :timeoutable, :trackable and :omniauthable
    devise :database_authenticatable, :registerable,
           :recoverable, :rememberable, :validatable
    has_many :friends
  end
  ```
- To associate datas we need to create `user_id` as well. For this we need to generate migration for the table
- example to add user_id to friends table which is int type and used as index:
  ```ruby
  rails g migration add_user_id_to_friends user_id:integer:index
  ```
  - on running the command on terminal output like this appears:
    ```ruby
    invoke  active_record
          create    db/migrate/20211007103414_add_user_id_to_friends.rb
    ```
  - to verify the migration navigate to the directory the terminal output is pointing to (highlighted in above snippet) and following codes should be seen:
    ```ruby
    class AddUserIdToFriends < ActiveRecord::Migration[6.1]
      def change
        add_column :friends, :user_id, :integer
        add_index :friends, :user_id
      end
    end
    ```
- to push migration :
  ```ruby
  rails db:migrate
  ```
- to verify migration navigate to `app>db>schema.rb` then following changes should be seen in respective table on last (friends in course):
  ```ruby
  create_table "friends", force: :cascade do |t|
      t.integer "user_id"
      t.index ["user_id"], name: "index_friends_on_user_id"
    end
  ```

### prepopulate user_id while creating data, creating friends in course

- `user_id` is being taken from `current_user` which is provided by devise gem
- `current_user.id` will give the `user_id`
- adding `user_id` to the form field which comes from `current_user.id:`
  ```html
  <div class="field">
  	<%= form.number_field :user_id, id: :friend_user_id, value:current_user.id,
  	type: :hidden, class:"form-control mb-3", placeholder:"phone" %>
  </div>
  ```
- passing `user_id` from form to the database:
  - we have to permit the `user_id` param to `params.require` field in <db_name>\_contorller.rb fille (`friend_controller.rb` in course)
    ```ruby
    def friend_params
          params.require(:friend).permit(:first_name, :last_name, :emial, :phone, :user_id)
        end
    ```

# More associations

- we are going to associate the one users friends to it's friends list and one user can be able to access their friends only
- we need to make sure that user is authenticated in order to change and view datas so we will be adding a `before_action` method in the respective controller file. `friends_controller.rb` in course

  - if user isn't authenticated then don't let them do anything except of seeing index and show pages

  ```ruby
  before_action : authenticate_user!, except:[:index , :show]
  ```

  - if the user is correct (admin/same as creator) then let them to edit the friend data. It can be done by using custom methods which is `correct_user` in course

    ```ruby
     before_action :correct_user, only: [:edit , :update , :destroy]

    def correct_user
      # params is the data got from form and param id is given by databse so it's used
      @friend = correct_user.friends.find(id: params[:id])
      # if the user is not found then @friend is going to be nil and if that happens data can't be edited
      redirect_to friends_path, notice: "Not authorized to edit this friend " if @friend.nil?
    end
    ```

### associate data according to user

- normally a new table `friends` in course is created with:
  ```ruby
  def new
      @friend = Friend.new
    end
  ```
- we need to create a data according to the user logged in. for that we do so that we can show the data according to the user logged in :
  ```ruby
  def new
  		# typical way to create data for schema
      # @friend = Friend.new
      # associating friend acc to user
      @friend =  correct_user.friends.build(friend_params)
    end
  ```
- showing database according to `user_id` only by:
  ```html
  <% if friend.user == current_user $>
  <tr>
  	<td><%= friend.first_name %></td>
  	<td><%= friend.last_name %></td>
  	<td><%= friend.emial %></td>
  	<td><%= friend.phone %></td>
  	<td><%= friend.user_id %></td>
  	<td><%= link_to 'Show', friend %></td>
  	<td><%= link_to 'Edit', edit_friend_path(friend) %></td>
  	<td>
  		<%= link_to 'Destroy', friend, method: :delete, data: { confirm: 'Are you
  		sure?' } %>
  	</td>
  </tr>
  <% end %>
  ```
